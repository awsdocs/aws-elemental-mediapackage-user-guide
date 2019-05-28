# Step 1: Create a Policy<a name="setting-up-create-trust-rel-policy"></a>

The IAM policy defines the permissions that AWS Elemental MediaPackage requires to access Amazon S3\. Create a policy that allows MediaPackage to read from the Amazon S3 bucket, verify the billing method, and retrieve content\. For the billing method, MediaPackage must verify that the bucket *does not* require the requester to pay for requests\. If the bucket has **requestPayment** enabled, MediaPackage can't ingest content from that bucket\.

**To use the JSON policy editor to create a policy**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation column on the left, choose **Policies**\. 

   If this is your first time choosing **Policies**, the **Welcome to Managed Policies** page appears\. Choose **Get Started**\.

1. At the top of the page, choose **Create policy**\.

1. Choose the **JSON** tab\.

1. Enter the following JSON policy document:

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
   ```

1. Choose **Review policy**\.
**Note**  
You can switch between the **Visual editor** and **JSON** tabs any time\. However, if you make changes or choose **Review policy** in the **Visual editor** tab, IAM might restructure your policy to optimize it for the visual editor\. For more information, see [Policy Restructuring](https://docs.aws.amazon.com/IAM/latest/UserGuide/troubleshoot_policies.html#troubleshoot_viseditor-restructure) in the *IAM User Guide*\.

1. On the **Review policy** page, enter a **Name** and an optional **Description** for the policy that you are creating\. Review the policy **Summary** to see the permissions that are granted by your policy\. Then choose **Create policy** to save your work\.