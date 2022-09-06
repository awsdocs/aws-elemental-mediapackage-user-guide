# Packager settings fields<a name="endpoints-hls-packager"></a>

The Packager settings fields hold general information about the endpoint\.

1. For **Packaging type**, choose **Apple HLS**\.

1. \(Optional\) For **Segment duration**, enter the duration \(in seconds\) of each segment\. Enter a value equal to, or a multiple of, the input segment duration\. If the value that you enter is different from the input segment duration, AWS Elemental MediaPackage rounds segments to the nearest multiple of the input segment duration\.

1. \(Optional\) For **Playlist window duration**, enter the total duration \(in seconds\) of the manifest\.

1. \(Optional\) To group all audio tracks into a single HLS rendition group, select **Use audio rendition group**\. For more information about rendition groups, see [Rendition groups reference in AWS Elemental MediaPackage](rendition-groups.md)\.

1. \(Optional\) To passthrough digital video broadcasting \(DVB\) subtitles into the output, select **Include DVB subtitles**\.

1. \(Optional\) To include an additional I\-frame only stream along with the other tracks in the manifest, select **Include IFrame only stream**\. MediaPackage generates an I\-frame only stream from the first rendition in the manifest\. The service inserts EXT\-I\-FRAMES\-ONLY tags in the output manifest, and then generates and includes an I\-frames only playlist in the stream\. This playlist enables player functionality like fast forward and rewind\.

1. \(Optional\) To include `EXT-X-PROGRAM-DATE-TIME` tags in the output manifest, select **Program date/time interval**, and then enter the interval for MediaPackage to insert the tags in the manifest\.

   The `EXT-X-PROGRAM-DATE-TIME` tag holds the time of the segment\. When program date time \(PDT\) information is available in the source content, MediaPackage uses this same information on the output content\. Otherwise, MediaPackage uses Coordinated Universal Time \(UTC\) for the PDT\.

   The PDT information helps downstream players to synchronize the stream to the wall clock, enabling functionality like viewer seek in the playback timeline and time display on the player\.

1. \(Optional\) For **Playlist type**, choose Event or VOD\. When specified as either event or VOD, a corresponding EXT\-X\-PLAYLIST\-TYPE entry is included in the media playlist\. Indicates if the playlist is live to VOD content\.

**SCTE\-35 Options**  
The following fields dictate how MediaPackage processes SCTE\-35 messages from the input stream\. For more information, see [SCTE\-35 message options in AWS Elemental MediaPackage](scte.md)\.

1. \(Optional\) In **Ad markers**, choose how ad markers are included in the packaged content\. 

   Choose from the following:
   + **None** – Omit all SCTE\-35 ad markers from the output\.
   + **SCTE\-35 enhanced** – Generate ad markers and blackout tags based on the SCTE\-35 input messages from the input source\.
   + **Passthrough** – Copy the SCTE\-35 ad markers directly from the input HLS input manifest to the output manifest\.

1. \(Optional\) To add or remove SCTE\-35 message types that MediaPackage treats as ads, choose **Customize ad triggers**\. If you don't make a selection here, MediaPackage inserts ad markers in the output manifest based on these message types:
   + Splice insert
   + Provider advertisement
   + Distributor advertisement
   + Provider placement opportunity
   + Distributor placement opportunity

1. \(Optional\) To change what ad insertion action MediaPackage takes based on delivery restriction flags in the segmentation descriptors of SCTE\-35 messages, choose **Ads on delivery restrictions**\. These are the available options:
   + **None** – MediaPackage doesn't insert any ad markers in the output manifest\.
   + **Restricted** – MediaPackage inserts ad markers when there *are* delivery restrictions in the SCTE\-35 message types that you indicated in **Customize ad triggers**\.
   + **Unrestricted** – MediaPackage inserts ad markers when there *aren't* delivery restrictions in the SCTE\-35 message types that you indicated in **Customize ad triggers**\.
   + **Both** – MediaPackage inserts ad markers whether or not there are delivery restrictions in the SCTE\-35 message types that you indicated in **Customize ad triggers**\.