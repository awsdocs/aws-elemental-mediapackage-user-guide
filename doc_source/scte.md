# SCTE\-35 message options in AWS Elemental MediaPackage<a name="scte"></a>

This section describes the options that AWS Elemental MediaPackage \(MediaPackage\) offers for configuring how SCTE\-35 messages are handled in live HLS, DASH, and CMAF outputs\. For live\-to\-VOD assets, MediaPackage passes the SCTE\-35 messages from the live stream through to the harvested asset\. These options don't apply to Microsoft Smooth Streaming or video on demand \(VOD\) outputs\. 

SCTE\-35 messages accompany video in your source content\. These messages signal where MediaPackage should insert ad markers when it packages the content for output\. By default, MediaPackage inserts markers for the following message types in the source content:
+ `splice_insert`
+ `time_signal` with the following segmentation types:
  + Provider advertisement
  + Distributor advertisement
  + Provider placement opportunity
  + Distributor placement opportunity

  The `time_signal` must also include delivery restriction flags in the `segmentation_descriptor`\.

When these commands are present, MediaPackage inserts corresponding ad markers in the output manifests:
+ For HLS and CMAF outputs, MediaPackage inserts `EXT-X-CUE-OUT` and `EXT-X-CUE-IN` tags\.
+ For DASH outputs, MediaPackage inserts `EventStream` tags to create multiple periods, when you have multi\-period manifests enabled\. 

The following sections describe how you can modify MediaPackage SCTE\-35 message handling behavior\.

## SCTE\-35 settings in MediaPackage<a name="scte-settings"></a>

You can modify how MediaPackage interacts with SCTE\-35 messages from your source content\. Configure the following settings on your endpoints\. For more information, see the following:
+ For the MediaPackage console, see [Creating an endpoint](endpoints-create.md)\.
+ For the MediaPackage API, see [Origin\_endpoints](https://docs.aws.amazon.com/mediapackage/latest/apireference/origin_endpoints.html) in the *AWS Elemental MediaPackage Live API Reference*\.

**Important**  
To modify how MediaPackage handles SCTE\-35 messages, you should be familiar with the SCTE\-35 standard\. You can view the most recent standards here: [SCTE Standards Catalog](https://www.scte.org/standards/library/catalog/)\. You should also be familiar with how SCTE\-35 is implemented in your source content\. 

****Ad markers****  
This setting is available on HLS and CMAF endpoints\.   
**Ad markers** allows you to specify what MediaPackage does when it detects SCTE\-35 messages\. These are the options:  
+ **None** – MediaPackage ignores the SCTE\-35 messages and doesn't include ad markers in the output manifest\.
+ **SCTE\-35 enhanced** – MediaPackage includes ad markers and blackout tags in the output manifest for SCTE\-35 messages that meet the requirements in **Customize ad triggers** and **Ads on delivery restrictions**\.
+ **Passthrough** – MediaPackage copies all SCTE\-35 messages from the source content and inserts them in the output manifest\.

****Customize ad triggers****  
This setting is available on HLS, DASH, and CMAF endpoints\.  
**Customize ad triggers** identifies which SCTE\-35 message types MediaPackage treats as ads in the output manifest\.   
If you don't change this setting, MediaPackage treats these message types as ads:  
+ Splice insert
+ Provider advertisement
+ Distributor advertisement
+ Provider placement opportunity
+ Distributor placement opportunity

****Ads on delivery restrictions****  
This setting is available on HLS, DASH, and CMAF endpoints\.  
**Ads on delivery restrictions** sets conditions for what SCTE\-35 messages become ads, based on the delivery restriction flags in the `segmentation_descriptor` of the messages\. MediaPackage inserts an ad marker that corresponds to the positioning of the messages of the right type that meet the delivery restriction conditions\.   
If you don't change this setting, MediaPackage converts messages that are classified as *restricted* \(they have delivery restriction flags\) to ad markers in the output manifest\.  
Splice insert SCTE\-35 messages don't have `segmentation_descriptor`\. If you choose splice insert in **Customize ad triggers**, all splice inserts become ad markers in the output manifest\.

## How it works<a name="scte-works"></a>

The **Ad markers**, **Customize ad triggers**, and **Ads on delivery restrictions** settings work together to determine what MediaPackage does with SCTE\-35 messages from the source content\.

When there are SCTE\-35 messages in the source content, MediaPackage takes the following action based on the value that you selected in **Ad markers**:
+ For **None**, MediaPackage does nothing with the SCTE\-35 messages\. No ad markers are inserted in the output manifest\.
+ For **Passthrough**, MediaPackage copies all SCTE\-35 messages from the source content and inserts them in the output manifest\.
+ For **SCTE\-35 enhanced**, MediaPackage checks for messages that meet the requirements that you set\. In the output manifest, MediaPackage inserts ad markers that correspond to the applicable messages\. To check for your requirements, MediaPackage does the following:

  1. Checks if any SCTE\-35 messages match the message types that you indicated in **Customize ad triggers**

  1. For messages of the right types, checks if the delivery restriction flags in `segmentation_descriptor` meet the conditions that you set in **Ads on delivery restrictions**

  1. For messages of the right type that meet the delivery restriction conditions, inserts ad markers in the output manifest, as described earlier in this chapter

  1. For **Daterange**, MediaPackage inserts `EXT-X-DATERANGE` tags to signal ads and program transition events in HLS and CMAF output manifests\.

## EXT\-X\-DATERANGE ad markers<a name="ext-x-daterange-ad-marker"></a>

Daterange ad markers are used to signal ads and program transitions in live HLS and CMAF manifests\. When you enable daterange ad markers on your endpoint, MediaPackage inserts `EXT-X-DATERANGE` tags into the manifest where there are SCTE\-35 `time_signal` or `splice_insert` tags present\. `EXT-X-DATERANGE` is used in concert with `EXT-X-PROGRAM-DATE-TIME` tags\. 

 For information about the `EXT-X-DATERANGE` and `EXT-X-PROGRAM-DATE-TIME` tags for HLS, see the [HTTP Live Streaming 2nd Edition Specification](https://tools.ietf.org/html/draft-pantos-hls-rfc8216bis-07#section-4.4.5.1)\. 

### Enabling daterange via the console<a name="enable-daterange-via-console"></a>

To enable daterange ad markers when creating or editing an endpoint, in the MediaPackage console, under **Packager settings** > **Additional configuration** > **Ad marker**, choose **Daterange**\.

If you choose Daterange, you *must* also enter a **Program date/time interval \(sec\)** value that's greater than **0**\. The program date/time interval is set in the same **Additional configuration** pane as the ad marker settings\. 

### Enabling daterange via the AWS CLI<a name="enable-daterange-via-cli"></a>

To enable daterange ad markers for your endpoint, run the following command in the AWS CLI replacing *region* with your own information:

```
  aws --endpoint=https://mediapackage.region.amazonaws.com mediapackage --region region create-origin-endpoint --channel-id test_channel --id hlsmuxed
  --hls-package "{\"ProgramDateTimeIntervalSeconds\":60,\"AdMarkers\":\"DATERANGE\"}"
```

**Important**  
You must set a `ProgramDateTimeIntervalSeconds` value that's greater than **0**\.

### Enabling daterange via the MediaPackage API or AWS SDK<a name="enable-daterange-via-live-api-or-sdk"></a>

 To learn how to enable daterange ad markers for HLS endpoints via the MediaPackage live API or AWS SDK, see the following: 
+ [MediaPackage Live API reference ](https://docs.aws.amazon.com/mediapackage/latest/apireference/origin_endpoints.html) 
+ [AWS SDK](https://aws.amazon.com/getting-started/tools-sdks/)

### Example HLS manifest showing SCTE\-35 EXT\-X\-DATERANGE signaling<a name="example"></a>

This example HLS manifest generated by MediaPackage uses `EXT-X-DATERANGE` and `EXT-X-PROGRAM-DATE-TIME` tags to signal events in the live stream\.

**Note**  
The `DURATION`, `PLANNED-DURATION`, and `END-DATE` attributes of the `EXT-X-DATERANGE` tag are optional\. If these attributes aren't present in the SCTE\-35 input, or aren't set when you create your endpoint via the MediaPackage API, then they are omitted from the generated manifests\.

```
#EXTM3U
#EXT-X-VERSION:3
#EXT-X-TARGETDURATION:8
#EXT-X-MEDIA-SEQUENCE:11
#EXT-X-DATERANGE:ID="2415919105",START-DATE="2020-05-03T00:01:00.018Z",PLANNED-DURATION=29.988,SCTE35-OUT=0xFC303000000002CDE400FFF00506FE00526C14001A021843554549900000017FC00000292EA80A04ABCD0001300000D6F17117
#EXT-X-DATERANGE:ID="2147483649",START-DATE="2020-05-03T00:00:30.030Z",PLANNED-DURATION=90.006,SCTE35-CMD=0xFC303000000002CDE400FFF00506FE00293D6C001A021843554549800000017FFF00007B9ABC0A04ABCD0001100000680F3B4B
#EXT-X-PROGRAM-DATE-TIME:2020-05-03T00:01:08.040Z
#EXTINF:7.560,
../../../../index_1_11.ts?m=1588607409
#EXTINF:7.560,
../../../../index_1_12.ts?m=1588607409
#EXTINF:6.846,
../../../../index_1_13.ts?m=1588607409
#EXT-X-DATERANGE:ID="2415919105",START-DATE="2020-05-03T00:01:00.018Z",END-DATE="2020-05-03T00:01:30.006Z",DURATION=29.988
#EXTINF:0.714,
../../../../index_1_14.ts?m=1588607409
#EXTINF:7.560,
../../../../index_1_15.ts?m=1588607409
#EXTINF:7.560,
../../../../index_1_16.ts?m=1588607409
#EXTINF:7.560,
../../../../index_1_17.ts?m=1588607409
#EXTINF:6.636,
../../../../index_1_18.ts?m=1588607409
#EXT-X-DATERANGE:ID="2147483649",START-DATE="2020-05-03T00:00:30.030Z",END-DATE="2020-05-03T00:02:00.036Z",DURATION=90.006,SCTE35-CMD=0xFC304A00000002CDE400FFF00506FE00A4D8280034021843554549800000017FC000000000000A04ABCD0001110000021843554549800000027FFF00007B9ABC0A04ABCD000210000061166A61
#EXT-X-DATERANGE:ID="2147483650",START-DATE="2020-05-03T00:02:00.036Z",PLANNED-DURATION=90.006,SCTE35-CMD=0xFC304A00000002CDE400FFF00506FE00A4D8280034021843554549800000017FC000000000000A04ABCD0001110000021843554549800000027FFF00007B9ABC0A04ABCD000210000061166A61
#EXTINF:0.924,
../../../../index_1_19.ts?m=1588607409
#EXTINF:7.560,
../../../../index_1_20.ts?m=1588607409
#EXT-X-PROGRAM-DATE-TIME:2020-05-03T00:02:08.520Z
#EXTINF:7.560,
../../../../index_1_21.ts?m=1588607409
#EXT-X-ENDLIST
```