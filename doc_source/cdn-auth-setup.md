# Setting up CDN authorization<a name="cdn-auth-setup"></a>

Complete the following steps to set up CDN authorization\.

**Topics**
+ [Step 1: Configure a CDN custom origin HTTP header](#cdn-aut-setup-cdn)
+ [Step 2: Store the value as a secret in AWS Secrets Manager](#cdn-aut-setup-secret)
+ [Step 3: Create an IAM policy and role for MediaPackage access to Secrets Manager](#cdn-aut-setup-iam)
+ [Step 4: Enable CDN authorization in MediaPackage](#cdn-aut-setup-endpoint)

## Step 1: Configure a CDN custom origin HTTP header<a name="cdn-aut-setup-cdn"></a>

In your CDN, configure a custom origin HTTP header that contains the header **X\-MediaPackage\-CDNIdentifier** and a value\. For the value, we recommend that you use the [UUID version 4](https://www.ietf.org/rfc/rfc4122.txt) format, which produces a 36\-character string\. If you aren't using the UUID version 4 format, the value must be 8\-128 characters long\.

**Important**  
The value you choose should be a static value\. There isn't native integration between your CDN and AWS Secrets Manager, so the value should be static both in your CDN and in AWS Secrets Manager\. If you change this value after you configure your CDN and your secret, you have to manually rotate the value\. For more information, see [Rotating the CDN header value](cdn-auth-rotate.md)\.

**Example header and value**

```
X-MediaPackage-CDNIdentifier: 9ceebbe7-9607-4552-8764-876e47032660
```

**To create a custom header in Amazon CloudFront**

1. Sign in to the AWS Management Console and open the CloudFront console at [https://console.aws.amazon.com/cloudfront/v3/home](https://console.aws.amazon.com/cloudfront/v3/home)\.

1. Create or edit a distribution\.

1. In **Origin Settings**, complete the fields\. You will use this same value for your secret in Secrets Manager\.
   + For **Header Name**, enter **X\-MediaPackage\-CDNIdentifier**\.
   + For **Value**, enter a value\. We recommend that you use UUID version 4 format, which produces a 36\-character string\. If you aren't using the UUID version 4 format, the value must be 8\-128 characters long\. 

1. Complete the rest of the fields and save the distribution\.

For more information about custom headers in CloudFront, see [Forwarding customer headers to your origin](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/forward-custom-headers.html) in the *Amazon CloudFront Developer Guide*\.

## Step 2: Store the value as a secret in AWS Secrets Manager<a name="cdn-aut-setup-secret"></a>

Store the same value that you use in your custom origin HTTP header as a *secret* in AWS Secrets Manager\. The secret must use the same AWS account and Region settings as your AWS Elemental MediaPackage resources\. MediaPackage doesn't support sharing secrets across accounts or Regions\. However, you can use the same secret across multiple endpoints in the same Region and on the same account\.

**To store a secret in Secrets Manager**

1. Sign in to the AWS Secrets Manager console at [https://console\.aws\.amazon\.com/secretsmanager/](https://console.aws.amazon.com/secretsmanager/)\.

1. Choose **Store a new secret**\. For **Select secret type**, choose **Other type of secrets**\.

1. For **Specify the key/value pairs to be stored in this secret**, choose **Secret key/pair**\.

1. Enter the key and value information\.
   + In the box on the left, enter **MediaPackageCDNIdentifier**\.
   + In the box on the right, enter the value that you configured for your custom origin HTTP header\. For example, `9ceebbe7-9607-4552-8764-876e47032660`\.

1. For **Select the encryption key**, you can keep the default value as **DefaultEncryptionKey**\.

1. Choose **Next**\.

1. For **Secret name**, we recommend that you prefix it with **MediaPackage/** so that you know it's a secret used for MediaPackage\. For example, **MediaPackage/cdn\_auth\_us\-west\-2**\.

1. Choose **Next**\.

1. For **Configure automatic rotation**, keep the default **Disable automatic rotation** setting\.

   If you need to rotate the authorization code later, see [Rotating the CDN header value](cdn-auth-rotate.md)\.

1. Choose **Next**, and then choose **Store**\.

   This takes you to the list of your secrets\.

1. Select your secret name to view the **Secret ARN**\. The ARN has a value similar to `arn:aws:secretsmanager:us-west-2:123456789012:secret:MediaPackage/cdn_auth_test-xxxxxx`\. You use the Secret ARN when you configure CDN authorization for MediaPackage in Step 4: Enable CDN Authorization in MediaPackage\. 

## Step 3: Create an IAM policy and role for MediaPackage access to Secrets Manager<a name="cdn-aut-setup-iam"></a>

Create an IAM policy and role to give MediaPackage read access to Secrets Manager\. When MediaPackage receives a playback request from the CDN, it verifies that the stored secret value matches the value in the custom HTTP header\. Follow the steps in [Allowing AWS Elemental MediaPackage to access other AWS services](setting-up-create-trust-rel.md) to set up the policy and role\.

## Step 4: Enable CDN authorization in MediaPackage<a name="cdn-aut-setup-endpoint"></a>

You can enable CDN authorization for your endpoints or video on demand \(VOD\) packaging groups via the console, AWS CLI, or MediaPackage API\. You use the Amazon Resource Numbers \(ARN\) for the IAM policy and role that you create in Step 3: Create an IAM policy and role for MediaPackage access to Secrets Manager\.

**Tip**  
Use the same secret across multiple endpoints in the same Region and on the same account\. Reduce costs by creating a new secret only when necessary for your workflow\.

**To enable CDN authorization for live content via the console**

1. Open the MediaPackage console at [https://console\.aws\.amazon\.com/mediapackage/](https://console.aws.amazon.com/mediapackage/)\.

1. If you don't already have a channel, create one\. For help, see [Creating a channel](channels-create.md)\.

1. Create or edit an endpoint\.

1. In **Access control settings**, select **Use authorization**\. Complete the fields:
   + In **Secrets role ARN**, enter the ARN for the IAM role that you created in [Step 3: Create an IAM policy and role for MediaPackage access to Secrets Manager](#cdn-aut-setup-iam)\.
   + In **CDN identifier secret**, enter the ARN for the secret that holds your authorization code in Secrets Manager\.

1. Complete the remaining fields as needed and save the endpoint\.

**To enable CDN authorization for VOD content via the console**

1. Open the MediaPackage console at [https://console\.aws\.amazon\.com/mediapackage/](https://console.aws.amazon.com/mediapackage/)\.

1. If you don't already have a VOD packaging group, create one\. For help, see [Creating a packaging group](pkg-group-create.md)\.

1. Create or edit a packaging group\.

1. In **Access control settings**, select **Use authorization**\. Complete the fields:
   + In **Secrets role ARN**, enter the ARN for the IAM role that you created in [Step 3: Create an IAM policy and role for MediaPackage access to Secrets Manager](#cdn-aut-setup-iam)\.
   + In **CDN identifier secret**, enter the ARN for the secret that holds your authorization code in Secrets Manager\.

1. Complete the remaining fields as needed and save the packaging group\.

You have now completed the setup for CDN authorization\. Requests to this endpoint must contain the same authorization code that you saved in Secrets Manager\.

**To enable CDN authorization via the MediaPackage API**  
For information about enabling CDN authorization with the MediaPackage API, see the following API references:
+ [MediaPackage live API reference](https://docs.aws.amazon.com/mediapackage/latest/apireference/resources.html)
+ [MediaPackage VOD API reference](https://docs.aws.amazon.com/mediapackage-vod/latest/apireference/)