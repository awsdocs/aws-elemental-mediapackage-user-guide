# Manifest settings fields<a name="cfigs-dash-manset"></a>

Specify the format of the manifest that AWS Elemental MediaPackage delivers from an asset that uses this packaging configuration\.

1. \(Optional\) For **Manifest name**, enter a short string that will be appended to the endpoint URL\. The manifest name helps to create a unique path to this endpoint\. If you don't enter a value, the default manifest name is *index*\.

1. \(Optional\) For **Min buffer time**, enter the minimum amount of time \(in seconds\) that a player must keep in the buffer\. If network conditions interrupt playback, the player will have additional buffered content before playback fails, allowing for recovery time before the viewer's experience is affected\.

1. \(Optional\) In **Profile**, specify a DASH profile, like HbbTV\.

   Choose from the following:
   + **None** – the output doesn't use a DASH profile
   + **Hbbtv 1\.5** – the output is HbbTV\-compliant

1. \(Optional\) In **Manifest layout**, choose if you want AWS Elemental MediaPackage to serve a full or compact manifest in response to playback requests\.
   + If you choose **Full**, MediaPackage presents the `SegmentTemplate` and `SegmentTimeline` tags for every `Representation` in the manifest\.
   + If you choose **Compact**, MediaPackage combines duplicate `SegmentTemplate` tags and presents them at the start of the manifest\. This shortens the manifest and makes it easier for some devices to process it\.

   For more information about the manifest layout options, see [Compacted DASH manifests](compacted.md)\.

1. \(Optional\) In **Segment template format**, choose how AWS Elemental MediaPackage and playback requests refer to each segment\.
   + If you choose **Number with timeline**, MediaPackage uses the `$Number$` variable to refer to the segment in the `media` attribute of the `SegmentTemplate` tag\. The value of the variable is the sequential number of the segment\. `SegmentTimeline` is included in each segment template\.
   + If you choose **Number with duration**, MediaPackage uses the `$Number$` variable and replaces the `SegmentTimeline` objects with a `duration` attribute in the segment template\.
**Note**  
This option isn't supported in combination with multi\-period DASH\.
   + If you choose **Time with timeline**, MediaPackage uses the `$Time$` variable to refer to the segment\. The value of the variable is the timestamp of when on the manifest timeline the segment starts\. `SegmentTimeline` is included in each segment template\.

   For more information about the formatting options of the `SegmentTemplate` tag, see [DASH manifest segment template format](segtemp-format.md)\.

1. For **Period triggers**, choose how AWS Elemental MediaPackage creates media presentation description \(MPD\) periods in the DASH output manifest\. Choose from the following:
   + **None** – MediaPackage doesn't create additional periods\. It formats the manifest as a single period and doesn't include SCTE\-35 markers in the segments\.
   + **Trigger new periods on ads** – MediaPackage creates and inserts in the manifest multiple periods based on SCTE\-35 ad markers from the input content\. These periods separate portions of the content, such as setting boundaries between the main content and ad content\. For more information about how AWS Elemental MediaPackage configures periods in the manifest, see [DASH manifest options in AWS Elemental MediaPackageMulti\-period DASH in AWS Elemental MediaPackage](multi-period.md)\.
**Important**  
Multiple periods are required if you use AWS Elemental MediaTailor for personalized ad insertion in DASH content\. For more information about this service, see the [AWS Elemental MediaTailor User Guide](https://docs.aws.amazon.com/mediatailor/latest/ug/)\.