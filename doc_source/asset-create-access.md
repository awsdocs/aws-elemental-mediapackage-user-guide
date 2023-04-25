# Asset access fields<a name="asset-create-access"></a>

The following fields describe how AWS Elemental MediaPackage accesses the source content in your Amazon S3 bucket\. MediaPackage must have permissions to access the bucket\. To create an IAM role with the right permissions, see [Allowing AWS Elemental MediaPackage to access other AWS services](setting-up-create-trust-rel.md)\.

1. For **Amazon S3 bucket name**, choose from a list of buckets that MediaPackage has detected in your account or enter the name of the bucket\. The Amazon S3 bucket holds the source content that MediaPackage ingests and packages for playback\. If you entered the name of the bucket, MediaPackage doesn't have visibility into this bucket, so it can't tell if the bucket is compatible or not\.
**Note**  
If you don't have permissions to view Amazon S3 buckets, MediaPackage doesn't display any options\. Contact your AWS administrator or enter the bucket name manually in the **Specify bucket name** field\.

1. For **IAM role**, choose the IAM role with the MediaPackage permissions to read from the Amazon S3 bucket\.
   + To choose from a list of roles that MediaPackage has detected on your account, choose **Use existing role** and choose the role\.
**Note**  
If you don't have permissions to view IAM roles, MediaPackage doesn't display any options\. Contact your AWS administrator or enter the role ARN manually in the **Specify custom role name** field\.
   + To use a role that MediaPackage hasn't detected, choose **Specify custom role name** and enter the custom ARN of the role\. Because MediaPackage doesn't have visibility into this role, it can't tell if the role provides the correct permissions or not\.