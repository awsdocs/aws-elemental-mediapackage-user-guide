# Setting up MediaPackage<a name="setting-up"></a>

Before you start using AWS Elemental MediaPackage \(MediaPackage\), you must sign up for AWS \(if you don’t already have an AWS account\) and create IAM users and roles to allow access to MediaPackage\. This includes creating an IAM role for yourself\. If you want to use encryption to protect your content, you also must store your encryption keys in AWS Secrets Manager, and then give MediaPackage permission to obtain the keys from your Secrets Manager account\.

This section guides you through the steps required to configure users and roles to access MediaPackage\. For background and additional information about identity and access management for MediaPackage, see [Identity and Access Management for AWS Elemental MediaPackage](security-iam.md)\.

**Topics**
+ [Signing up for AWS](setting-up-aws-sign-up.md)
+ [Creating policies and non\-administrative roles](setting-up-create-non-admin-iam.md)
+ [Allowing AWS Elemental MediaPackage to access other AWS services](setting-up-create-trust-rel.md)
+ [\(Optional\) Setting up encryption](set-up-encryption.md)
+ [\(Optional\) Install the AWS CLI](setting-up-install-cli.md)