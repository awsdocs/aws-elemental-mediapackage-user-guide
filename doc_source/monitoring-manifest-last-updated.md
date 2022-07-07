# Monitoring manifest update time<a name="monitoring-manifest-last-updated"></a>

AWS Elemental MediaPackage playback responses include the following custom headers that indicate when MediaPackage last modified the manifest in non\-dynamic ad insertion workflows\. These headers are helpful when troubleshooting issues related to stale manifests\.

## X\-MediaPackage\-Manifest\-Last\-Sequence<a name="manifest-last-sequence"></a>

This is the highest segment sequence number in the manifest\.
+ For DASH, this is the highest segment number in the lowest rendition of the manifest\.
+ For HLS and CMAF, this is the highest segment number in the media playlist\.
+ For MSS, this is the highest segment number in the manifest\.

See the following section for [manifest examples](#manifest-examples)\.

## X\-MediaPackage\-Manifest\-Last\-Updated<a name="manifest-last-updated"></a>

The epoch timestamp in milliseconds when MediaPackage generates the segment referred to in `X-MediaPackage-Manifest-Last-Sequence`\.

## Manifest examples<a name="manifest-examples"></a>



### DASH manifest examples<a name="dash-examples"></a>

For both compact and full DASH manifests, MediaPackage determines the `X-MediaPackage-Manifest-Last-Sequence` value from the highest segment number in the lowest rendition of the manifest\. The service calculates the `X-MediaPackage-Manifest-Last-Updated` value based on when it generates the segment referred to in `X-MediaPackage-Manifest-Last-Sequence`\.

#### Number with duration \- compact manifest<a name="collapsible-section-1"></a>

The following is an example of a compact DASH manifest that uses the number with duration template\. MediaPackage determines the `X-MediaPackage-Manifest-Last-Sequence` value from the highest segment number in the lowest rendition in the manifest\. For example, in the following manifest, the highest segment number is `index_video_5_0_175232.mp4`, so the value of `X-MediaPackage-Manifest-Last-Sequence` is `175232`\. See [`duration` Attribute in the `SegmentTemplate`](segtemp-format-duration.md) for information about how MediaPackage calculates the sequence `$Number$` value\. The value of `X-MediaPackage-Manifest-Last-Updated` is the epoch timestamp in milliseconds when MediaPackage generates the segment referred to in `X-MediaPackage-Manifest-Last-Sequence`\.

```
<?xml version="1.0" encoding="utf-8"?>
<MPD xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="urn:mpeg:dash:schema:mpd:2011" xsi:schemaLocation="urn:mpeg:dash:schema:mpd:2011 http://standards.iso.org/ittf/PubliclyAvailableStandards/MPEG-DASH_schema_files/DASH-MPD.xsd" id="201" type="dynamic" publishTime="2021-09-08T21:01:38" minimumUpdatePeriod="PT0S" availabilityStartTime="2018-11-16T19:08:30Z+00:00" minBufferTime="PT0S" suggestedPresentationDelay="PT0.000S" timeShiftBufferDepth="PT116.533S" profiles="urn:mpeg:dash:profile:isoff-live:2011">
  <Period start="PT0.000S" id="1">
    <AdaptationSet mimeType="video/mp4" segmentAlignment="true" subsegmentAlignment="true" startWithSAP="1" subsegmentStartsWithSAP="1" bitstreamSwitching="true">
        <SegmentTemplate timescale="30000" media="index_video_$RepresentationID$_0_$Number$.mp4?m=1543947824" initialization="index_video_$RepresentationID$_0_init.mp4?m=1543947824" startNumber="175032" duration="90000"/>
        <Representation id="1" width="640" height="360" frameRate="30/1" bandwidth="749952" codecs="avc1.640029"/>
        <Representation id="2" width="854" height="480" frameRate="30/1" bandwidth="1000000" codecs="avc1.640029"/>
        <Representation id="3" width="1280" height="720" frameRate="30/1" bandwidth="2499968" codecs="avc1.640029"/>
    </AdaptationSet>
</Period>
</MPD>
```

#### Number with timeline \- compact manifest<a name="collapsible-section-2"></a>

The following is an example of a compact DASH manifest that uses the number with timeline template\. MediaPackage determines the `X-MediaPackage-Manifest-Last-Sequence` value from the highest segment number in the lowest rendition in the manifest\. For example, in the following manifest, the highest segment number is `index_video_1_0_7.mp4`, so the value of `X-MediaPackage-Manifest-Last-Sequence` is `7`\. The value of `X-MediaPackage-Manifest-Last-Updated` is the is the epoch timestamp in milliseconds when MediaPackage generates the segment referred to in `X-MediaPackage-Manifest-Last-Sequence`\.

```
<?xml version="1.0" encoding="utf-8"?>
<MPD xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="urn:mpeg:dash:schema:mpd:2011" xsi:schemaLocation="urn:mpeg:dash:schema:mpd:2011 http://standards.iso.org/ittf/PubliclyAvailableStandards/MPEG-DASH_schema_files/DASH-MPD.xsd" id="201" type="static" mediaPresentationDuration="PT72.458S" minBufferTime="PT0S" profiles="urn:mpeg:dash:profile:isoff-main:2011">
  <Period start="PT0.000S" id="1" duration="PT74.758S">
    <AdaptationSet mimeType="video/mp4" segmentAlignment="true" startWithSAP="1" subsegmentAlignment="true" subsegmentStartsWithSAP="1" bitstreamSwitching="true">
      <SegmentTemplate timescale="48000" media="index_video_$RepresentationID$_0_$Number$.mp4?m=1621616401" initialization="index_video_$RepresentationID$_0_init.mp4?m=1621616401" startNumber="1" presentationTimeOffset="108800">
        <SegmentTimeline>
          <S t="110400" d="540000" r="5"/>
          <S t="3350400" d="238000"/>
        </SegmentTimeline>
      </SegmentTemplate>
      <Representation id="1" width="640" height="480" frameRate="24/1" bandwidth="5000000" codecs="avc1.4D401E"/>
    </AdaptationSet>
    <AdaptationSet mimeType="audio/mp4" segmentAlignment="0" lang="eng">
      <Label>eng</Label>
      <SegmentTemplate timescale="48000" media="index_audio_$RepresentationID$_0_$Number$.mp4?m=1621616401" initialization="index_audio_$RepresentationID$_0_init.mp4?m=1621616401" startNumber="1" presentationTimeOffset="108800">
        <SegmentTimeline>
          <S t="108800" d="541696"/>
          <S t="650496" d="540672"/>
          <S t="1191168" d="539648" r="1"/>
          <S t="2270464" d="540672"/>
          <S t="2811136" d="539648"/>
          <S t="3350784" d="236544"/>
        </SegmentTimeline>
      </SegmentTemplate>
      <Representation id="2" bandwidth="192000" audioSamplingRate="48000" codecs="mp4a.40.2">
        <AudioChannelConfiguration schemeIdUri="urn:mpeg:dash:23003:3:audio_channel_configuration:2011" value="2"></AudioChannelConfiguration>
      </Representation>
    </AdaptationSet>
    <SupplementalProperty schemeIdUri="urn:scte:dash:utc-time" value="2021-05-21T16:59:47.450Z"></SupplementalProperty>
  </Period>
</MPD>
```

#### Number with timeline \- compact manifest<a name="collapsible-section-2"></a>

The following is an example of a compact DASH manifest that uses the number with duration template\. MediaPackage determines the `X-MediaPackage-Manifest-Last-Sequence` value from the highest segment number in the lowest rendition in the manifest\. For example, in the following manifest, the highest segment number is `index_video_1_0_1675200.mp4`, so the value of `X-MediaPackage-Manifest-Last-Sequence` is `1675200`\. See [`media` Attribute in `SegmentTemplate`](segtemp-format-media.md) for information about how MediaPackage calculates the sequence number\. The value of `X-MediaPackage-Manifest-Last-Updated` is the is the epoch timestamp in milliseconds when MediaPackage generates the segment referred to in `X-MediaPackage-Manifest-Last-Sequence`\.

```
<?xml version="1.0" encoding="utf-8"?>
<MPD xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="urn:mpeg:dash:schema:mpd:2011" xsi:schemaLocation="urn:mpeg:dash:schema:mpd:2011 http://standards.iso.org/ittf/PubliclyAvailableStandards/MPEG-DASH_schema_files/DASH-MPD.xsd" id="201" type="static" mediaPresentationDuration="PT72.458S" minBufferTime="PT0S" profiles="urn:mpeg:dash:profile:isoff-main:2011">
  <Period start="PT0.000S" id="1" duration="PT74.758S">
    <AdaptationSet mimeType="video/mp4" segmentAlignment="true" startWithSAP="1" subsegmentAlignment="true" subsegmentStartsWithSAP="1" bitstreamSwitching="true">
      <SegmentTemplate timescale="48000" media="index_video_$RepresentationID$_0_$Time$.mp4?m=1621616401" initialization="index_video_$RepresentationID$_0_init.mp4?m=1621616401" startNumber="1" presentationTimeOffset="108800">
        <SegmentTimeline>
          <S t="55200" d="270000" r="5"/>
          <S t="1675200" d="119000"/>
        </SegmentTimeline>
      </SegmentTemplate>
      <Representation id="1" width="640" height="480" frameRate="24/1" bandwidth="5000000" codecs="avc1.4D401E"/>
    </AdaptationSet>
    <AdaptationSet mimeType="audio/mp4" segmentAlignment="0" lang="eng">
      <Label>eng</Label>
      <SegmentTemplate timescale="48000" media="index_audio_$RepresentationID$_0_$Time$.mp4?m=1621616401" initialization="index_audio_$RepresentationID$_0_init.mp4?m=1621616401" startNumber="1" presentationTimeOffset="108800">
        <SegmentTimeline>
          <S t="108800" d="541696"/>
          <S t="650496" d="540672"/>
          <S t="1191168" d="539648" r="1"/>
          <S t="2270464" d="540672"/>
          <S t="2811136" d="539648"/>
          <S t="3350784" d="236544"/>
        </SegmentTimeline>
      </SegmentTemplate>
      <Representation id="2" bandwidth="192000" audioSamplingRate="48000" codecs="mp4a.40.2">
        <AudioChannelConfiguration schemeIdUri="urn:mpeg:dash:23003:3:audio_channel_configuration:2011" value="2"></AudioChannelConfiguration>
      </Representation>
    </AdaptationSet>
    <SupplementalProperty schemeIdUri="urn:scte:dash:utc-time" value="2021-05-21T16:59:47.450Z"></SupplementalProperty>
  </Period>
</MPD>
```

### HLS manifest<a name="hls-examples"></a>

MediaPackage determines the `X-MediaPackage-Manifest-Last-Sequence` value from the last segment in the manifest\. For example, in the following manifest `index_1_3.ts` is the highest segment sequence number, so the value of `X-MediaPackage-Manifest-Last-Sequence` is `3`\. The value of `X-MediaPackage-Manifest-Last-Updated` corresponds to the epoch timestamp in milliseconds when MediaPackage generates the last segment in the manifest\.

```
#EXTM3U
#EXT-X-VERSION:3
#EXT-X-TARGETDURATION:8
#EXT-X-MEDIA-SEQUENCE:0
#EXTINF:7.500,
index_1_0.ts?m=1583172400
#EXTINF:7.500,
index_1_1.ts?m=1583172400
#EXTINF:7.500,
index_1_2.ts?m=1583172400
#EXTINF:7.500,
index_1_3.ts?m=1583172400
#EXT-X-ENDLIST
```

### CMAF manifest<a name="hls-example"></a>

Similar to HLS, MediaPackage determines the `X-MediaPackage-Manifest-Last-Sequence` value from the last segment in the manifest\. For example, in the following manifest `../cmafseg_video_1_10.mp4?m=1621616399` is the highest segment sequence number, so the value of `X-MediaPackage-Manifest-Last-Sequence` is `10`\. The value of `X-MediaPackage-Manifest-Last-Updated` corresponds to the epoch timestamp in milliseconds when MediaPackage generates the last segment in the manifest\.

```
#EXTM3U
#EXT-X-VERSION:6
#EXT-X-INDEPENDENT-SEGMENTS
#EXT-X-TARGETDURATION:12
#EXT-X-MEDIA-SEQUENCE:1
#EXT-X-MAP:URI="../cmafseg_video_1_track_1098178399_csid_aaa_2_init.mp4"
#EXTINF:11.250,
../cmafseg_video_1_1.mp4?m=1621616399
#EXTINF:11.250,
../cmafseg_video_1_2.mp4?m=1621616399
#EXTINF:11.250,
../cmafseg_video_1_3.mp4?m=1621616399
#EXTINF:11.250,
../cmafseg_video_1_4.mp4?m=1621616399
#EXTINF:11.250,
../cmafseg_video_1_5.mp4?m=1621616399
#EXTINF:11.250,
../cmafseg_video_1_6.mp4?m=1621616399
#EXTINF:11.250,
../cmafseg_video_1_7.mp4?m=1621616399
#EXTINF:11.250,
../cmafseg_video_1_8.mp4?m=1621616399
#EXTINF:11.250,
../cmafseg_video_1_9.mp4?m=1621616399
#EXTINF:0.542,
../cmafseg_video_1_10.mp4?m=1621616399
#EXT-X-ENDLIST
```

### MSS manifest<a name="mss-examples"></a>

MediaPackage determines the `X-MediaPackage-Manifest-Last-Sequence` value from the highest segment in the manifest, as indicated by `Fragments(a_2_0={start time})`\. For example, in the following manifest `Fragments(a_2_0=380533333)` is the highest sequence number, so the value of `X-MediaPackage-Manifest-Last-Sequence` is `380333333`\. The value of `X-MediaPackage-Manifest-Last-Updated` corresponds to the epoch timestamp in milliseconds when MediaPackage generates the last segment in the manifest\.

```
<SmoothStreamingMedia MajorVersion="2" MinorVersion="2" TimeScale="10000000" CanSeek="TRUE" CanPause="TRUE" IsLive="TRUE" LookAheadFragmentCount="2" DVRWindowLength="3000000000" Duration="0">
  <CustomAttributes>
    <Attribute Name="ProducerReferenceTime" Value="2017-06-14T22:07:01.967Z"/>
  </CustomAttributes>
  <StreamIndex Type="video" Name="video" Subtype="" Chunks="3" TimeScale="10000000" Url="Events(203_0)/QualityLevels({bitrate})/Fragments(v={start time})" QualityLevels="1">
    <QualityLevel Index="0" Bitrate="4000000" CodecPrivateData="00000001274D401F924602802DD80880000003008000001E7220007A120000895477BDC07C22114E0000000128FEBC80" FourCC="H264" MaxWidth="1280" MaxHeight="720"/>
    <c d="120000000" t="20333333"/>
    <c d="120000000"/>
    <c d="120000000"/>
  </StreamIndex>
  <StreamIndex Type="audio" Name="fra_1" Language="fra" Subtype="" Chunks="3" TimeScale="10000000" Url="Events(203_0)/QualityLevels({bitrate})/Fragments(a_2_0={start time})">
    <QualityLevel Index="0" Bitrate="128460" CodecPrivateData="1190" FourCC="AACL" AudioTag="255" Channels="2" SamplingRate="48000" BitsPerSample="16" PacketSize="4"/>
    <c d="120533333" t="20000000"/>
    <c d="119893333"/>
    <c d="120106667"/>
  </StreamIndex>
</SmoothStreamingMedia>
```