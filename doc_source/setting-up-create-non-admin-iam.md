# Creating policies and non\-administrative roles<a name="setting-up-create-non-admin-iam"></a>

By default, users and roles don't have permission to create or modify MediaPackage resources\. They also can't perform tasks by using the AWS Management Console, AWS Command Line Interface \(AWS CLI\), or AWS API\. To grant users permission to perform actions on the resources that they need, an IAM administrator can create IAM policies\. The administrator can then add the IAM policies to roles, and users can assume the roles\.

To learn how to create an IAM identity\-based policy by using these example JSON policy documents, see [Creating IAM policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_create-console.html) in the *IAM User Guide*\.

For details about actions and resource types defined by MediaPackage, including the format of the ARNs for each of the resource types, see [Actions, resources, and condition keys for AWS Elemental MediaPackage](https://docs.aws.amazon.com/service-authorization/latest/reference/list_awselementalmediapackage.html) in the *Service Authorization Reference*\.

This section describes how you can create policies and create non\-administrative roles so that users can create or modify MediaPackage resources\. This section also describes how your users can assume that role to grant secure and temporary credentials\.

**Topics**
+ [\(Optional\) Step 1: Create an IAM policy for Amazon CloudFront](setting-up-create-non-admin-iam-cf.md)
+ [\(Optional\) Step 2: Create an IAM policy for MediaPackage VOD](setting-up-create-non-admin-iam-vod.md)
+ [Step 3: Create a role in the IAM console](setting-up-create-role.md)
+ [Step 4: Assume the role from the IAM console or AWS CLI](setting-up-create-nonadmin-roles-assume-role.md)