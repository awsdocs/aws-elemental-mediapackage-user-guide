# Step 3: Create a role in the IAM console<a name="setting-up-create-role"></a>

Create a role in the IAM console for each policy that you create\. This allows users to assume a role rather than attaching individual policies to each user\.

**To create a role in the IAM console**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane of the IAM console, choose **Roles**, and then choose **Create role**\.

1. Under **Select trusted entity**, choose **AWS account**\.

1. Under **An AWS account**, select the account with the users that will be assuming this role\.
   + If a third\-party will be accessing this role, it's best practice to select **Require external ID**\. For more information about external IDs, see [Using an external ID for third\-party access](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_create_for-user_externalid.html) in the *IAM User Guide*\.
   + It's best practice to require multi\-factor authentication \(MFA\)\. You can select the check box next to **Require MFA**\. For more information about MFA, see [Multi\-factor authentication \(MFA\)](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_mfa.html) in the *IAM User Guide*\.

1. Choose **Next**\.

1. Under **Permissions policies**, search for and add the policy with the appropriate MediaPackage permissions level\.
   + For access to live functionality, choose one of the following options:
     + Use **AWSElementalMediaPackageFullAccess** to allow the user to perform all actions on all live resources in MediaPackage\.
     + Use **AWSElementalMediaPackageReadOnly** to provide the user read\-only rights for all live resources in MediaPackage\.
   + For access to video on demand \(VOD\) functionality, use the policy that you created in [\(Optional\) Step 2: Create an IAM policy for MediaPackage VOD](setting-up-create-non-admin-iam-vod.md)\.

1. Add policies to allow the MediaPackage console to make calls to Amazon CloudWatch on the user's behalf\. Without these policies, the user is able to use the service's API only \(not the console\)\. Choose one of the following options:
   + Use **ReadOnlyAccess** to allow MediaPackage to communicate with CloudWatch, and also provide the user read\-only access to all AWS services on your account\.
   + Use **CloudWatchReadOnlyAccess**, **CloudWatchEventsReadOnlyAccess**, and **CloudWatchLogsReadOnlyAccess** to allow MediaPackage to communicate with CloudWatch, and limit the user's read\-only access to CloudWatch\.

1. \(Optional\) If this user will create Amazon CloudFront distributions from the MediaPackage console, attach the policy that you created in [\(Optional\) Step 1: Create an IAM policy for Amazon CloudFront](setting-up-create-non-admin-iam-cf.md)\.

1. \(Optional\) Set a [permissions boundary](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_boundaries.html)\. This is an advanced feature that is available for service roles, but not service\-linked roles\. 

   1. Expand the **Permissions boundary** section and choose **Use a permissions boundary to control the maximum role permissions**\. IAM includes a list of the AWS managed and customer managed policies in your account\.

   1. Select the policy to use for the permissions boundary or choose **Create policy** to open a new browser tab and create a new policy from scratch\. For more information, see [Creating IAM policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_create.html#access_policies_create-start) in the *IAM User Guide*\.

   1. After you create the policy, close that tab and return to your original tab to select the policy to use for the permissions boundary\.

1. Verify that the correct policies are added to this group, and then choose **Next**\.

1. If possible, enter a role name or role name suffix to help you identify the purpose of this role\. Role names must be unique within your AWS account\. They are not distinguished by case\. For example, you cannot create roles named both **PRODROLE** and **prodrole**\. Because various entities might reference the role, you cannot edit the name of the role after it has been created\.

1. \(Optional\) For **Description**, enter a description for the new role\.

1. Choose **Edit** in the **Step 1: Select trusted entities** or **Step 2: Select permissions** sections to edit the use cases and permissions for the role\. 

1. \(Optional\) Add metadata to the user by attaching tags as key\-value pairs\. For more information about using tags in IAM, see [Tagging IAM resources](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_tags.html) in the *IAM User Guide*\.

1. Review the role and then choose **Create role**\.