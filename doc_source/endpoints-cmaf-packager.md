# Packager settings fields<a name="endpoints-cmaf-packager"></a>

The Packager settings fields hold general information about the endpoint\.

1. For **Packaging type**, choose **Common Media Application Format \(CMAF\)**\. 

1. For **HLS Manifest ID**, enter an ID that will be the primary identifier for the manifest\. The ID must be unique for this endpoint\. You cannot change this ID after it's created\.

1. \(Optional\) For **Segment prefix**, enter a custom name for the segments in the HLS child manifest\. The segment prefix is prepended to the segment name to create a unique identifier for each segment\.  
**Example**  

   If the segment prefix is `movie`, a segment from the child manifest is `movie_1_2.ts`\.

1. \(Optional\) For **Segment duration**, enter the duration \(in seconds\) of each segment\. Enter a value equal to, or a multiple of, the input segment duration\. If the value that you enter is different from the input segment duration, AWS Elemental MediaPackage rounds segments to the nearest multiple of the input segment duration\.

1. \(Optional\) For **Live playlist window duration**, enter the total duration \(in seconds\) of the parent manifest\.

1. For **Manifest name**, enter a string that will be appended to the end of the endpoint URL\. The manifest name helps to create a unique path to this manifest on this endpoint\. The HLS manifest name overrides the manifest name that you provided in the New Endpoint** Manifest name** field \(if applicable\)\.

1. \(Optional\) Select **Include IFrame only stream** to include an additional I\-frame only stream along with the other tracks in the manifest\. MediaPackage generates an I\-frame only stream from the first rendition in the manifest\. The service inserts `EXT-I-FRAMES-ONLY` tags in the output manifest, and then compiles and includes an I\-frames only playlist in the stream\. This playlist enables player functionality like fast forward and rewind\.

1. \(Optional\) For **Program date/time interval**, enter the interval \(in seconds\) at which MediaPackage should insert the `EXT-X-PROGRAM-DATE-TIME` tags in the manifest\.

   The `EXT-X-PROGRAM-DATE-TIME` tag holds the time of the segment\. When program date time \(PDT\) information is available in the source content, MediaPackage uses this same information on the output content\. Otherwise, MediaPackage uses Coordinated Universal Time \(UTC\) for the PDT\.

   The PDT information helps downstream players to synchronize the stream to the wall clock, enabling functionality like viewer seek in the playback timeline and time display on the player\.

1. \(Optional\) For **Playlist type**, choose **None**, **Event**, or **VOD**\. When speciﬁed as either event or VOD, a corresponding `EXT-X-PLAYLIST-TYPE` entry is included in the media playlist\. Indicates if the playlist is live to VOD content\.

1. \(Optional\) Use the following fields to dictate how MediaPackage processes SCTE\-35 messages from the input stream\. For more information, see [SCTE\-35 message options in AWS Elemental MediaPackage](scte.md)\. 

   1. \(Optional\) For **Ad markers**, choose how ad markers are included in the packaged content\. 

      Choose from the following:
      + **None** – Omit all SCTE\-35 ad markers from the output\.
      + **Passthrough** – Copy the SCTE\-35 ad markers directly from the input HLS input stream to the output\.
      + **SCTE\-35 enhanced** – Generate ad markers and blackout tags in the output based on the SCTE\-35 input messages from the input stream\.
      + **Daterange** – Emit `EXT-X-DATERANGE` tags in HLS and CMAF manifests to signal ads and program transitions\.

   1. \(Optional\) For **Ad triggers**, choose the SCTE\-35 message types that you want to be treated as ad markers in the output\. If you don't make a selection here, MediaPackage inserts ad markers in the output manifest based on these message types:
      + Splice insert
      + Provider advertisement
      + Distributor advertisement
      + Provider placement opportunity
      + Distributor placement opportunity

   1. \(Optional\) For **Ads on delivery restrictions**, choose what ad insertion action MediaPackage takes based on delivery restriction flags in the segmentation descriptors of SCTE\-35 messages\.
      + **None** – MediaPackage doesn't insert any ad markers in the output manifest\.
      + **Restricted** – MediaPackage inserts ad markers when there *are* delivery restrictions in the SCTE\-35 message types that you indicated in **Customize ad triggers**\.
      + **Unrestricted** – MediaPackage inserts ad markers when there *aren't* delivery restrictions in the SCTE\-35 message types that you indicated in **Customize ad triggers**\.
      + **Both** – MediaPackage inserts ad markers whether or not there are delivery restrictions in the SCTE\-35 message types that you indicated in **Customize ad triggers**\.