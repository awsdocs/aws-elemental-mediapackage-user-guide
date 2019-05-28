# Step 2: Create a Packaging Group<a name="gs-create-grp"></a>

A packaging group holds one or more packaging configurations\. The group enables you to define what kind of outputs you want, and then to apply these output definitions to multiple assets\. For example, you have 15 pieces of source content\. You want them all to serve DASH, HLS, and encrypted HLS outputs, so you define one packaging group with these types of packaging configurations\. You then select that group on all the assets\. You don't have to create a new configuration for each asset\.

**To create a packaging group**

1. On the AWS Elemental MediaPackage **Packaging groups** page, choose **Create**\.

1. For **ID**, enter a name that describes the group, such as **kidsmovies** \. The ID is the primary identifier for the group, and must be unique for your account in this AWS Region\. Supported characters are letters, numbers, underscore \(\_\), and dash \(\-\)\. You can't use spaces in the ID\.

1. Choose **Create**\.