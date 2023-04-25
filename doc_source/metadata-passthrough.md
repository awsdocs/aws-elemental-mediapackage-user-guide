# Metadata passthrough<a name="metadata-passthrough"></a>

AWS Elemental MediaPackage automatically passes through ID3 and key\-length\-value \(KLV\) metadata from a channel's input to the channel's output stream\. You don't need to adjust your endpoint's configuration to enable metadata passthrough\.

For more information about how MediaPackage handles metadata, see the following sections\.

**Topics**
+ [ID3 metadata considerations](#metadata-passthrough-id3)
+ [KLV metadata considerations](#metadata-passthrough-klv)

## ID3 metadata considerations<a name="metadata-passthrough-id3"></a>

Timed ID3 metadata is a general\-purpose mechanism that adds synchronized metadata to streams\. The metadata is used for a variety of purposes, ranging from interactive applications to audience measurement\.

**Supported MediaPackage endpoint types**

MediaPackage supports ID3 metadata passthrough for the following endpoint types:
+ Live and VOD HLS, DASH, and CMAF endpoints

**Metadata carriage**

Here is how ID3 is carried as metadata in the following specifications:
+ HLS \- Metadata is carried in the elementary stream\. For more information, see [section 2\.0](https://developer.apple.com/library/archive/documentation/AudioVideo/Conceptual/HTTP_Live_Streaming_Metadata_Spec/2/2.html) of the Apple *Timed Metadata for HTTP Live Streaming* reference\.
+ CMAF and DASH \- Metadata is carried in the Event Message box version 1\. For more information, see [Carriage of ID3 Timed Metadata in CMAF](https://aomediacodec.github.io/id3-emsg/)\. Event Message boxes include a `scheme_id_uri` field set to `https://aomedia.org/emsg/ID3` and a `value` field set to `0`\.

**Metadata signaling**

DASH manifests include a `<InbandEventStream schemeIdUri="https://aomedia.org/emsg/ID3" value="0"/>` element in AdaptationSets that include tracks with ID3 metadata\. 

HLS manifests don't have specific metadata signaling\.

**MediaLive** **configuration**

You can produce ID3 metadata in AWS Elemental MediaLive[ MediaPackage output groups](https://docs.aws.amazon.com/medialive/latest/ug/creating-mediapackage-output-group.html) either by [passing through ID3 metadata](https://docs.aws.amazon.com/medialive/latest/ug/passthru-metadata.html), or [inserting ID3 metadata using the schedule](https://docs.aws.amazon.com/medialive/latest/ug/insert-usercreated-metadata.html)\.

## KLV metadata considerations<a name="metadata-passthrough-klv"></a>

KLV is a data encoding standard for including synchronized metadata in streams\. The binary nature of KLV makes it efficient when the volume of metadata is significant\. KLV can be used for various use cases ranging from aerial surveillance to transmitting sensors data in industry use cases, or for real\-time athlete and object tracking in live sports use cases\.

**Supported MediaPackage endpoint types**

MediaPackage supports KLV metadata passthrough for the following endpoint types:
+ Live DASH endpoints

**Metadata carriage**

Metadata is carried in the Event Message box version 1, as described in the *[MISB ST 1910\.1](https://nsgreg.nga.mil/doc/view?i=5097) specification*\. For synchronous KLV tracks, Event Message boxes include a `scheme_id_uri` field set to `urn:misb:KLV:bin:1910.1` and a `value` field set to `KLVx:01FC`\. For asynchronous KLV tracks, the value field is set to `KLVx:01BD`\. In both cases, `x` is the index of the track in the stream\.

**Metadata signaling**

DASH manifests include a `<InbandEventStream schemeIdUri="urn:misb:KLV:bin:1910.1" value="KLVx:01FC"/>` or `<InbandEventStream schemeIdUri="urn:misb:KLV:bin:1910.1" value="KLVx:01BD"/>` element in AdaptationSets that include tracks with KLV metadata, depending on the synchronicity nature of the carried track\.

**MediaLive** **configuration**

You can pass through KLV metadata from your MediaLive channel\. For more information, see [https://docs.aws.amazon.com/medialive/latest/apireference/channels.html#channels-prop-m2tssettings-klv](https://docs.aws.amazon.com/medialive/latest/apireference/channels.html#channels-prop-m2tssettings-klv) in the *AWS Elemental MediaLive User Guide*\.