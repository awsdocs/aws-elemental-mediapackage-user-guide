# Step 4: Create an asset<a name="gs-create-asset"></a>

An asset resource is how MediaPackage ingests, packages, and serves VOD content\. The asset is associated with one or more packaging configurations\. Downstream devices send playback requests to specific packaging configurations on the asset\.

MediaPackage does not require that you supply any customer data\. There are no fields in assets where there is an expectation that you will provide customer data\.

**To create an asset**

1. From your Amazon S3 buckets, determine what file you're using as source content\. Make note of the following:
   + The name of the Amazon S3 bucket where the file is stored
   + The full path for the file, such as *S3://bucket/path/source\-file\-name*
   + The IAM role that allows MediaPackage to read from Amazon S3

1. On the MediaPackage console, go to the **Assets** page, and then choose **Ingest assets**\.

1. For **Amazon S3 bucket name**, choose the bucket where your source content is stored\.

1. For **IAM role**, choose **Use existing role** and select the IAM role that allows MediaPackage to read from Amazon S3\.

1. For **Filename**, enter the full path to either the \.smil manifest \(MP4\) or the \.m3u8 parent playlist \(HLS\) within your Amazon S3 bucket, including the name of the source content\. You don't need to enter the bucket name because you chose it in **Amazon S3 bucket name** field\. For example, if your content is called` lion_movie.m3u8` and is in a subdirectory called `thursday_night` in a bucket called `movies`, you would enter the following in the **Filename** field:

   ```
   thursday_night/lion_movie.m3u8
   ```

   For more information about using \.smil manifests with MediaPackage, see [Requirements for \.smil manifests](supported-inputs-vod-smil.md)\.

1. For **Packaging group**, choose the group that you created in [Step 2: Create a packaging group](gs-create-grp.md)\.

1. Choose **Ingest assets**\.