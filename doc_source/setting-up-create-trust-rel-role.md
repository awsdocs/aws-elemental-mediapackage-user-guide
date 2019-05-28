# Step 2: Create a Role<a name="setting-up-create-trust-rel-role"></a>

  An [IAM role](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles.html) is an IAM identity that you can create in your account that has specific permissions\. An IAM role is similar to an IAM user in that it is an AWS identity with permissions policies that determine what the identity can and cannot do in AWS\. However, instead of being uniquely associated with one person, a role is intended to be assumable by anyone who needs it\. Also, a role does not have standard long\-term credentials such as a password or access keys associated with it\. Instead, when you assume a role, it provides you with temporary security credentials for your role session\. Create a role that AWS Elemental MediaPackage assumes when ingesting source content from Amazon S3\.

When you create the role, you choose EC2 as the trusted entity that can assume the role because AWS Elemental MediaPackage isn't available for selection\. In [Step 3: Modify the Trust Relationship](setting-up-create-trust-rel-trust.md), you change the trusted entity to MediaPackage\.

**To create the service role for an EC2 \(IAM console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane of the IAM console, choose **Roles**, and then choose **Create role**\.

1. Choose the **AWS service** role type, and then choose EC2\.

1. Choose the EC2 use case\. Then choose **Next: Permissions**\.

1. On the **Attach permissions policies** page, search for and choose the policy that you created in [ Step 1: Create a Policy  The IAM policy defines the permissions that AWS Elemental MediaPackage requires to access Amazon S3\. Create a policy that allows MediaPackage to read from the Amazon S3 bucket, verify the billing method, and retrieve content\. For the billing method, MediaPackage must verify that the bucket *does not* require the requester to pay for requests\. If the bucket has **requestPayment** enabled, MediaPackage can't ingest content from that bucket\.  To use the JSON policy editor to create a policy Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.  In the navigation column on the left, choose **Policies**\.  If this is your first time choosing **Policies**, the **Welcome to Managed Policies** page appears\. Choose **Get Started**\.   At the top of the page, choose **Create policy**\.   Choose the **JSON** tab\.   Enter the following JSON policy document: 

   ```
   {
       "Version": "2012-10-17",
       "Statement": [
           {
               "Action": [
                   "s3:GetObject",
                   "s3:GetBucketLocation",
                   "s3:GetBucketRequestPayment"
               ],
               "Resource": [
                   "arn:aws:s3:::{bucket_name}/*",
                   "arn:aws:s3:::{bucket_name}"
               ],
               "Effect": "Allow"
           }
       ]
   }
   ```   Choose **Review policy**\.  You can switch between the **Visual editor** and **JSON** tabs any time\. However, if you make changes or choose **Review policy** in the **Visual editor** tab, IAM might restructure your policy to optimize it for the visual editor\. For more information, see [Policy Restructuring](https://docs.aws.amazon.com/IAM/latest/UserGuide/troubleshoot_policies.html#troubleshoot_viseditor-restructure) in the *IAM User Guide*\.    On the **Review policy** page, enter a **Name** and an optional **Description** for the policy that you are creating\. Review the policy **Summary** to see the permissions that are granted by your policy\. Then choose **Create policy** to save your work\.   ](setting-up-create-trust-rel-policy.md)\. Then choose **Next: Tags** and **Next: Review**\.

1. \(Optional\) Set a [permissions boundary](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_boundaries.html)\. This is an advanced feature that is available for service roles, but not service\-linked roles\. 

   Expand the **Set permissions boundary** section and choose **Use a permissions boundary to control the maximum role permissions**\. IAM includes a list of the AWS managed and customer managed policies in your account\. Select the policy to use for the permissions boundary or choose **Create policy** to open a new browser tab and create a new policy from scratch\. For more information, see step 4 in the procedure [Creating IAM policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_create.html#access_policies_create-start) in the *IAM User Guide*\. After you create the policy, close that tab and return to your original tab to select the policy to use for the permissions boundary\.

1. Choose **Next: Tags**\.

1. \(Optional\) Add metadata to the user by attaching tags as key\-value pairs\. For more information about using tags in IAM, see [Tagging IAM Entities](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_tags.html) in the *IAM User Guide*\.

1. Choose **Next: Review**\.

1. If possible, enter a role name or role name suffix to help you identify the purpose of this role\. Role names must be unique within your AWS account\. They are not distinguished by case\. For example, you cannot create roles named both **PRODROLE** and **prodrole**\. Because various entities might reference the role, you cannot edit the name of the role after it has been created\.

1. \(Optional\) For **Role description**, enter a description for the new role\.

1. Review the role and then choose **Create role**\.