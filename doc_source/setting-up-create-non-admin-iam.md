# Creating a Non\-Admin IAM User<a name="setting-up-create-non-admin-iam"></a>

Users in the Administrators group for an account have access to all AWS services and resources in that account\. This section describes how to create users with permissions that are limited to AWS Elemental MediaPackage\.

**To create users who can access AWS Elemental MediaPackage**

1. In the navigation pane of the IAM console, choose **Users**, and then choose **Add user**\.

1. For **User name**, type the name that the user will use to sign in to AWS Elemental MediaPackage\.

1. Select the check box next to **AWS Management Console access**, select **Custom password**, and then type the new user's password in the box\. You can optionally select **Require password reset** to force the user to create a password the next time the user signs in\.

1. Choose **Next: Permissions**\.

1. On the **Set permissions for user** page, choose **Attach existing policies directly**\.

1. In the policy list, search for and add the policy with the appropriate AWS Elemental MediaPackage permissions level:
   + Use **AWSElementalMediaPackageFullAccess** to allow the user to perform all actions on all resources in AWS Elemental MediaPackage\.
   + Use **AWSElementalMediaPackageReadOnly** to provide the user read\-only rights for all resources in AWS Elemental MediaPackage\.

1. Add policies to allow the AWS Elemental MediaPackage console to make calls to Amazon CloudWatch on the user's behalf\. Without these policies, the user is able to use the service's API only \(not the console\)\. Choose one of these options:
   + Use **ReadOnlyAccess** to allow AWS Elemental MediaPackage to communicate with CloudWatch, and also provide the user read\-only access to all AWS services on your account\.
   + Use **CloudWatchReadOnlyAccess**, **CloudWatchEventsReadOnlyAccess**, and **CloudWatchLogsReadOnlyAccess** to allow AWS Elemental MediaPackage to communicate with CloudWatch, and limit the user's read\-only access to CloudWatch\.

1. \(Optional\) If this user will create Amazon CloudFront distributions from the AWS Elemental MediaPackage console, create and attach a policy that provides required permissions for the user\. The policy looks like this:

   ```
   {
       "Version": "2012-10-17",
       "Statement": [
           {
               "Effect": "Allow",
               "Action": [
                   "cloudfront:GetDistribution",
                   "cloudfront:CreateDistributionWithTags",
                   "cloudfront:UpdateDistribution",
                   "tag:GetResources"
               ],
               "Resource": "*"
           }
       ]
   }
   ```

   For help creating the policy, see [Creating a Policy for Amazon CloudFront](setting-up-create-non-admin-iam-cf.md)\.

1. Choose **Next: Review** to see the list of policies to be added to the new user\. When you are ready to proceed, choose **Create user**\.