# VOD supported codecs and input types<a name="supported-inputs-vod"></a>

The following sections describe supported input types and codecs for file\-based video on demand \(VOD\) content\.

## Supported input types<a name="supported-types-vod"></a>

These are the input types that AWS Elemental MediaPackage supports for VOD content\.


| MediaPackage input type | Use case | 
| --- | --- | 
| HLS | Pull an HLS stream set from an Amazon Simple Storage Service bucket, with or without a secure connection\.Additional requirements:[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/mediapackage/latest/ug/supported-inputs-vod.html) | 
| SMIL | Pull an MP4 stream set referenced by a \.smil manifest from an Amazon Simple Storage Service bucket, with or without a secure connection\. For information about the \.smil manifest, see [Requirements for \.smil manifests](supported-inputs-vod-smil.md)\.Additional requirements:[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/mediapackage/latest/ug/supported-inputs-vod.html) | 

## Supported input codecs<a name="suported-inputs-codecs-vod"></a>

These are the video, audio, and subtitles codecs that MediaPackage supports for file\-based source content\.


| Input type | Media container | Video codecs | Audio codecs | Subtitles/captions format | 
| --- | --- | --- | --- | --- | 
| HLS |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/mediapackage/latest/ug/supported-inputs-vod.html)  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/mediapackage/latest/ug/supported-inputs-vod.html)  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/mediapackage/latest/ug/supported-inputs-vod.html)  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/mediapackage/latest/ug/supported-inputs-vod.html)  | 
| SMIL | MP4 \(non\-fragmented\) |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/mediapackage/latest/ug/supported-inputs-vod.html)  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/mediapackage/latest/ug/supported-inputs-vod.html)  | SRT | 

## Supported output codecs<a name="suported-outputs-codecs-vod"></a>

These are the video, audio, and subtitles codecs that MediaPackage supports for delivering VOD content\.


| Endpoint type | Manifest format | Media container | Video codecs | Audio codecs | Subtitles/captions format | 
| --- | --- | --- | --- | --- | --- | 
| Apple HLS | HLS |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/mediapackage/latest/ug/supported-inputs-vod.html)  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/mediapackage/latest/ug/supported-inputs-vod.html)  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/mediapackage/latest/ug/supported-inputs-vod.html)  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/mediapackage/latest/ug/supported-inputs-vod.html)  | 
| Microsoft Smooth | MSS | MP4 |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/mediapackage/latest/ug/supported-inputs-vod.html)  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/mediapackage/latest/ug/supported-inputs-vod.html)  | DFXP | 
| DASH\-ISO | MPEG\-DASH | MP4 |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/mediapackage/latest/ug/supported-inputs-vod.html)  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/mediapackage/latest/ug/supported-inputs-vod.html)  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/mediapackage/latest/ug/supported-inputs-vod.html)  | 
| CMAF | HLS | CMAF |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/mediapackage/latest/ug/supported-inputs-vod.html)  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/mediapackage/latest/ug/supported-inputs-vod.html)  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/mediapackage/latest/ug/supported-inputs-vod.html)  | 