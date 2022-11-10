# Manifest properties<a name="manifest-properties"></a>

These are the main properties in a manifest that determine if it's live or VOD:
+ For HLS and CMAF VOD manifests, `EXT-X-ENDLIST` is at the end of the bitrate manifests\. In live manifests, this tag isn't present\.
+ For MPEG\-DASH VOD manifests, `type="static"` is in the `MPD` properties\. In live manifests, `type=dynamic`\.
+ For Microsoft Smooth VOD manifests, `IsLive` isn't present in the `SmoothStreamingMedia` properties\. In live manifests, `IsLive=TRUE`\.

For VOD, the scrub bar on playback devices also often shows that the program has a limited duration\. This duration is equal to the length of the current manifest\. If a playback request defines a specific playback window, this duration is equal to the length of that playback window\. 