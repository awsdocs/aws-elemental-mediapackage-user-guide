# Asset details fields<a name="asset-create-details"></a>

The following fields describe the source content that this asset uses\.

If you have multiple sources for this asset, choose **Add asset** and complete the fields\. Do this for all source contents\.

**Important**  
Source content must be in a \.smil \(MP4\) or \.m3u8 \(HLS/TS\) file format\.

1. For **Filename**, Enter the full path to either the \.smil manifest \(MP4\) or the \.m3u8 parent playlist \(HLS\) within your Amazon S3 bucket, including the name of the source content\. You don't need to enter the bucket name because you chose it in **S3 bucket name** field\. For example, if your content is called` lion_movie.m3u8` and is in a subdirectory called `thursday_night` in a bucket called `movies`, you would enter the following in the **Filename** field:

   ```
   thursday_night/lion_movie.m3u8
   ```

   For more information about using \.smil manifests with MediaPackage, see [Requirements for \.smil manifests](supported-inputs-vod-smil.md)\.

1. For **ID**, enter a name that describes the asset\. The ID is the primary identiﬁer for the asset, and must be unique for your account in this Region\. Supported characters are letters, numbers, underscores \(\_\), and dashes \(\-\)\.

1. \(Optional\) For **Resource ID**, enter an identifier for the content\. When you're using SPEKE, the resource ID is the identifier that your key server uses to reference the content\. MediaPackage sends the ID to the key server to identify the current asset\. How unique you make the ID depends on the level of access controls you need\. The service doesn't allow you to use the same ID for two simultaneous encryption processes\. The resource ID is also known as the content ID\.  
**Example**  

   ```
   MovieNight20171126093045
   ```