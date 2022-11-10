# Working with trick\-play in AWS Elemental MediaPackage<a name="trick-play"></a>

Trick\-play, sometimes called trick mode, provides a visual cue to viewers as they rewind, fast\-forward, or seek through content in a digital video player\. This helps the person using the video player to visualize where they are in the content timeline\.

AWS Elemental MediaPackage supports I\-frame and image\-based trick\-play for live and video on demand \(VOD\) workflows\. For I\-frame trick\-play, MediaPackage generates an I\-frame track from the first rendition in your HLS multivariant playlist\. For image\-based trick\-play, MediaPackage passes through the image media playlist that you configure in your upstream encoder\. To learn how to use I\-frame and image\-based trick\-play for MediaPackage, see the sections in this topic\.

MediaPackage supports the following trick\-play types:

**Supported trick\-play types for live workflows**


| Streaming protocol | I\-frame only | Image\-based | 
| --- | --- | --- | 
|  Apple HLS  |  √  |  √  | 
|  CMAF Apple HLS  |  √  |  √  | 
|  DASH  |  √  |  √  | 

**Supported trick\-play types for VOD workflows**


| Streaming protocol | I\-frame only | Image\-based | 
| --- | --- | --- | 
|  Apple HLS  |  √  |    | 
|  CMAF Apple HLS  |  √  |    | 
|  DASH  |  √  |  √  | 

**Topics**
+ [Using I\-frame playlists to enable trick\-play](#using-i-frame-playlists)
+ [Using image media playlists to enable trick\-play](#using-image-media-playlists)

## Using I\-frame playlists to enable trick\-play<a name="using-i-frame-playlists"></a>

MediaPackage supports live and on\-demand trick\-play by creating an I\-frame playlist from an existing VOD asset or live stream\. The I\-frame playlist contains the I\-frame only video segments that your player uses for the image thumbnails\. For information about I\-frame playlists, see the HTTP Live Streaming 2nd Edition specification: [https://datatracker.ietf.org/doc/html/rfc8216#section-4.3.3.6](https://datatracker.ietf.org/doc/html/rfc8216#section-4.3.3.6)\.

**To use an I\-frame playlist to enable trick\-play**
+ To use I\-frame playlists to enable trick\-play, in the MediaPackage console choose **Include I\-frame only stream** when creating or editing an endpoint or packaging configuration\. MediaPackage generates an I\-frame only stream from the first rendition in the manifest\. The service inserts `EXT-I-FRAMES-ONLY` tags in the output manifest, and then generates and includes an I\-frames only playlist in the stream\. This playlist enables player functionality like fast forward and rewind\.

## Using image media playlists to enable trick\-play<a name="using-image-media-playlists"></a>

To use image\-based trickplay, in your upstream encoder you create an HLS *image media playlist* that contains JPEG image segments\. MediaPackage automatically passes through the image segments to the output\. These segments are the thumbnail images and image metadata that the video player uses for visual cues\. These segments must conform to the [Image Media Playlist specification, version 0\.4](https://github.com/image-media-playlist/spec/blob/master/image_media_playlist_v0_4.pdf)\. The service supports the time\-based implementation of the specification\.

For information about how to configure your upstream encoder to generate an image media playlist, see [Configuring your upstream encoder to generate image media playlists](#configuring-upstream-encoder)\.

### Input source requirements<a name="image-based-requirements"></a>

Your HLS source content must meet the following requirements:
+ The HLS parent playlist that references the image playlist must include the `#EXT-X-IMAGE-STREAM-INF` tag\.
+ The image playlist must include the following tags:
  + An `#EXT-X-IMAGES-ONLY` tag above the segment list\.
  + If using tiled thumbnails, `#EXT-X-TILES` tags above each image segment that specifies the tiling information\. Tiled thumbnails are only available for VOD workflows\.
**Note**  
We recommend that you use decimal durations in the `#EXT-INF` and `#EXT-X-TILES` tags to help MediaPackage give players the most accurate image durations\.
+ You must use image segments that are valid JPEG image files less than 20 MB\. For tiled thumbnails, the image segments can be tiled, with multiple thumbnails in a grid in the JPEG, or a single tile can occupy the entire JPEG\.
  + For live, each JPEG must contain only one image segment\. The encoder must produce image segments and video segments at the same cadence\.

You can use AWS Media Services to generate an HLS source in your upstream encoder that complies with the Image Media Playlist specification, version 0\.4\. For more information, see the following section [Configuring your upstream encoder to generate image media playlists](#configuring-upstream-encoder)\.

#### Limitations<a name="image-based-limitations"></a>

Keep in mind the following limitations when using image\-based trick\-play for MediaPackage:
+ MediaPackage doesn't combine image segments for packaging configurations\. For example, if the service ingests a VOD asset with an image asset with a 2 second segment duration, and you specify a segment output duration of 6 seconds, we combine the video and audio segments to be 6 seconds long, but image segments will remain 2 seconds\.
+ Depending on your HLS player requirements, the use of `#EXT-X-PROGRAM-DATE-TIME` tags might be necessary to display the trick\-play image\. This applies to live and VOD workflows\.

### Considerations when using image\-based trick\-play for DASH<a name="trickplay-dash-considerations"></a>

MediaPackage supports single or tiled thumbnails for VOD workflows, and single thumbnails for live workflows\. Your HLS content must conform to the [Image Media Playlist specification, version 0\.4](https://github.com/image-media-playlist/spec/blob/master/image_media_playlist_v0_4.pdf)\. See the following paragraph for specific requirements\. When MediaPackage outputs content from a DASH packaging configuration or endpoint, the service outputs thumbnails based on the [DASH\-IF Interoperability Points](https://dashif.org/docs/DASH-IF-IOP-v4.3.pdf) specification, v4\.3, section 6\.2\.6\.

In addition to the general requirements listed before this section, keep in mind the following requirements and limitations when using trick\-play for DASH\.
+ MediaPackage only supports DASH tiled thumbnails for VOD workflows\.
+ In general, the service doesn't support multi\-period DASH for packaging configurations that use `NUMBER_WITH_DURATION` because it impacts segment alignment\. This limitation also applies to trick\-play\.
+ The service generates the image segment time format for live and VOD as follows:
  + For live, the image segment's time format is the same as your endpoint's time format for audio and video segments\. This format is set by the **segment template format** on your endpoint\. For example, if your endpoint has a segment template format of `NUMBER_WITH_TIMELINE`, the image segment uses `NUMBER_WITH_TIMELINE` for the time format\.
  + For VOD, the image segment uses `NUMBER_WITH_DURATION` regardless of which time format you set for your packaging configuration\. For example, if you choose the `NUMBER_WITH_TIMELINE` segment template format for your packaging configuration, the service will use `NUMBER_WITH_TIMELINE` for video and audio Adaptation Sets, but will use `NUMBER_WITH_DURATION` for the image Adaptation Sets\.

### Configuring your upstream encoder to generate image media playlists<a name="configuring-upstream-encoder"></a>

Your HLS source must conform to the [Image Media Playlist specification, version 0\.4](https://github.com/image-media-playlist/spec/blob/master/image_media_playlist_v0_4.pdf)\. You can use the following AWS Media Services to create an HLS stream that complies with the specification\. For more information, see the following documentation:
+ [Trick\-play track via the Image Media Playlist specification](https://docs.aws.amazon.com/elemental-live/latest/ug/trick-play-roku.html) in the *Elemental Live User Guide*\.
+ [Trick\-play track via the Image Media Playlist specification](https://docs.aws.amazon.com/medialive/latest/ug/trick-play-roku.html) in the *AWS Elemental MediaLive User Guide*\.
+ [HlsImageBasedTrickPlay](https://docs.aws.amazon.com/mediaconvert/latest/apireference/jobs.html#jobs-prop-hlsgroupsettings-imagebasedtrickplay) in the *AWS Elemental MediaConvert API Reference*\.