# Manifest filtering<a name="manifest-filtering"></a>

With manifest filtering, MediaPackage dynamically produces client manifests based on parameters that you specify in a query appended to your playback request\. This enables you to do things such as restrict viewer access to premium 4K HEVC content, or target specific device types and audio sample rate ranges, all from a single endpoint\. Previously, you would have to configure multiple endpoints to accomplish this behavior\. MediaPackage now provides a cost\-effective way to dynamically produce different client manifests on the same endpoint\.

## Working with manifest filters<a name="working-with-manifest-filters"></a>

When you use a manifest filter, the resulting manifest includes only the audio and video streams that match the characteristics that you specify in your query\. If no manifest filter is used, then all of the ingested streams are present in the endpoint output stream\. The exception to this is if you have set stream filters for the endpoint, such as minimum video bitrate\. In that case, the manifest filter is applied after the stream filter, which could skew your output, and is not recommended\.

Manifest filtering can be used on all endpoint types supported by MediaPackage:
+ Apple HLS
+ DASH\-ISO
+ Microsoft Smooth Streaming
+ CMAF

To use manifest filtering, append `aws.manifestfilter` query parameters to your playback request to MediaPackage\. MediaPackage evaluates the query, and serves a client manifest based on those query parameters\. Manifest queries are *not *case\-sensitive and can be up to 1024 characters long\. If the query is malformed, or if it there aren't streams that match the query parameters, MediaPackage returns an incomplete or empty manifest\. For query syntax, see the following section\.

**Note**  
If you are using Apple HLS or CMAF endpoints, special conditions apply\. For information about these conditions, see [Special conditions for HLS and CMAF manifests](#special-conditions-HLS-CMAF-manifests)\.

**Query syntax**  
The base query parameter is `aws.manifestfilter`, which is followed by optional parameter name and value pairs\. To construct the query, append `?aws.manifestfilter=` to the end of the MediaPackage endpoint URL, followed by parameter names and values\. For a list of all of the available parameters, see [Manifest filter query parameters](#manifest-filter-query-parameters)\.

An Apple HLS filter query might look like this:

`https://example-mediapackage-endpoint.mediapackage.us-west-2.amazonaws.com/out/v1/examplemediapackage/index.m3u8?aws.manifestfilter=audio_sample_rate:0-44100;video_bitrate:0-2147483647;video_codec:h265;audio_language:fr,en-US,de`

The query syntax is listed in the following table\.


| Query string component | Description | 
| --- | --- | 
| ? | A restricted character that marks the beginning of a query\. | 
| aws\.manifestfilter= | The base query, which is followed by parameters constructed of name and value pairs\. For a list of all of the available parameters, see [Manifest filter query parameters](#manifest-filter-query-parameters)\. | 
| : | Used to associate the parameter name with a value\. For example, parameter\_name:value\. | 
| ; | Separates parameters in a query that contains multiple parameters\. For example, parameter1\_name:value;parameter2\_name:minValue\-maxValue\. | 
| , | Separates a list of values\. For example, parameter\_name:value1,value2,value3\. Comma\-separated values in a list imply an OR relationship\. | 
| \- | Used to define a parameter's minimum \- maximum value range\. For example, audio\_sample\_rate:0\-44100\. When a numerical value is used in a range, it is included in the range definition\. This means that streams must be greater than or equal to the minimum value, and less than or equal to the maximum value\. With ranges, the minimum and maximum values are mandatory\. The supported range values are 0 \- 2147483647\. | 

**Note**  
If you use Amazon CloudFront as your CDN, you might need to set additional configurations\. For more information, see [Configure cache behavior for all endpoints\.](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/live-streaming.html#live-streaming-with-mediapackage-create-cache-behavior)\.

## Manifest filter query parameters<a name="manifest-filter-query-parameters"></a>

MediaPackage supports the following query parameters\.


| Category | Name | Description | Example | 
| --- | --- | --- | --- | 
| Audio | audio\_bitrate |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/mediapackage/latest/ug/manifest-filtering.html)  | stream\.mpd?aws\.manifestfilter=audio\_bitrate:0\-2147483647 | 
| Audio | audio\_channels |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/mediapackage/latest/ug/manifest-filtering.html)  | stream\.mpd?aws\.manifestfilter=audio\_channels:1\-8 | 
| Audio | audio\_codec |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/mediapackage/latest/ug/manifest-filtering.html)  | stream\.mpd?aws\.manifestfilter=audio\_codec:AACL,AC\-3 | 
| Audio | audio\_language |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/mediapackage/latest/ug/manifest-filtering.html)  | stream\.mpd?aws\.manifestfilter=audio\_language:fr,en\-US,de | 
| Audio | audio\_sample\_rate |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/mediapackage/latest/ug/manifest-filtering.html)  | stream\.mpd?aws\.manifestfilter=audio\_sample\_rate:0\-44100 | 
| Subtitle | subtitle\_language |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/mediapackage/latest/ug/manifest-filtering.html)  | stream\.mpd?aws\.manifestfilter=subtitle\_language:en\-US, hi | 
| Video | trickplay\_height |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/mediapackage/latest/ug/manifest-filtering.html)  | stream\.mpd?aws\.manifestfilter=trickplay\_height:200\-1200 | 
| Video | trickplay\_type |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/mediapackage/latest/ug/manifest-filtering.html)  | stream\.mpd?aws\.manifestfilter=trickplay\_type:iframe | 
| Video | video\_bitrate |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/mediapackage/latest/ug/manifest-filtering.html)  | stream\.mpd?aws\.manifestfilter=video\_bitrate:0\-2147483647 | 
| Video | video\_codec |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/mediapackage/latest/ug/manifest-filtering.html)  | stream\.mpd?aws\.manifestfilter=video\_codec:h264 | 
| Video | video\_dynamic\_range |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/mediapackage/latest/ug/manifest-filtering.html)  | stream\.mpd?aws\.manifestfilter=video\_dynamic\_range:hdr10 | 
| Video | video\_framerate |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/mediapackage/latest/ug/manifest-filtering.html)  | stream\.mpd?aws\.manifestfilter=video\_framerate:23\.976\-30 | 
| Video | video\_height |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/mediapackage/latest/ug/manifest-filtering.html)  | stream\.mpd?aws\.manifestfilter=video\_height:720\-1080 | 

## Manifest filtering examples<a name="manifest-filtering-examples"></a>

These are manifest filtering examples\.

**Example 1: Target a player that supports AVC and a 44\.1k audio sample rate**  
The viewer is playing content on a device that can only support AVC and a 44\.1k audio sample rate\. You set the `video_codec` and `audio_sample_rate` to filter out streams that don't fit these requirements\.

`?aws.manifestfilter=audio_sample_rate:0-44100;video_codec:h264`

**Example 2: Restrict 4k HEVC content**  
Your 4K HEVC stream is 15 Mbps, and all your other streams are less than 9 Mbps\. To exclude the 4K stream from the stream set, you set a threshold of 9,000,000 bits per second to filter out the higher bitrate\.

`?aws.manifestfilter=video_bitrate:0-9000000`

**Example 3: Include video between 23\.976 and 30 frames per second**  
To only include video within a certain frame rate range, use `video_framerate`\. This parameter accepts floating\-point numbers with up to three optional decimal values\.

`?aws.manifestfilter=video_framerate:23.976-30`

## Special conditions for HLS and CMAF manifests<a name="special-conditions-HLS-CMAF-manifests"></a>

If you are using HLS or CMAF manifests, these special conditions apply\.
+ For HLS manifests, we strongly recommend that you use audio rendition groups to avoid removing the video streams that are multiplexed with the audio streams that are filtered out\. For more information about rendition groups, see [Rendition groups reference in AWS Elemental MediaPackage](rendition-groups.md)\.
+ In HLS and CMAF manifests, the audio sample rate is not signaled, so it's not easy to visually check the original or filtered manifests for this setting\. To verify the audio sample rate, check the audio sample rate at the encoder level and output level\.
+ In HLS and CMAF manifests, the `BANDWIDTH` attribute for a variant associates the bandwidth of the audio track with the video track, whether it is multiplexed with the video track, or if it is an audio rendition track referenced by the video track\. Therefore, you can't visually inspect the original and filtered manifests to confirm the `video_bitrate` filter has worked\. To verify the filter, check the video bitrate at the encoder level and output level\.
+ For HLS and CMAF manifests, request parameters appended to bitrate playlists or segments result in an HTTP 400 error\.

## Error conditions<a name="error-conditions-and-handling"></a>

Common error conditions are listed in the following table\. 


****  

| Error condition | Example | HTTP status code | 
| --- | --- | --- | 
| A list parameter is not found and is not part of a constrained list | ?aws\.manifestfilter=audio\_language:dahlia | 200 | 
| Only subtitle streams are present in the stream | ?aws\.manifestfilter=audio\_sample\_rate:0\-1;video\_bitrate=0\-1 | 200 | 
| Duplicate filter parameter | ?aws\.manifestfilter=audio\_sample\_rate:0\-48000;aws\.manifestfilter=audio\_sample\_rate:0\-48000 | 400 | 
| Invalid parameter | ?aws\.manifestfilter=donut\_type:rhododendron | 400 | 
| Invalid range parameter | ?aws\.manifestfilter=audio\_sample\_rate:300\-0 | 400 | 
| Invalid range value \(more than INT\_MAX\) | ?aws\.manifestfilter=audio\_sample\_rate:0\-2147483648 | 400 | 
| Malformed query string | ?aws\.manifestfilter=audio\_sample\_rate:is:0\-44100 | 400 | 
| Parameter string is greater than 1024 characters | ?aws\.manifestfilter=audio\_language:abcdef\.\.\.\. | 400 | 
| Query parameters on an HLS or CMAF bitrate manifest | index\_1\.m3u8?aws\.manifestfilter=video\_codec:h264 | 400 | 
| Query parameters on a segment request | \.\.\.\_1\.\[ts\|mp4\|vtt\.\.\]?aws\.manifestfilter=video\_codec:h264 | 400 | 
| Repeated query parameter | ?aws\.manifestfilter=audio\_sample\_rate:0\-48000;aws\.manifestfilter=video\_bitrate:0\-1 | 400 | 
| Application of the filter results in an empty manifest \(content has no streams that meet the conditions defined in the query string\) | ?aws\.manifestfilter=audio\_sample\_rate:0\-1;video\_bitrate=0\-1 | 400 | 