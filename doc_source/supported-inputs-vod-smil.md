# Requirements for \.smil manifests<a name="supported-inputs-vod-smil"></a>

When you send an VOD MP4 asset to AWS Elemental MediaPackage, you must include a \.smil manifest\. The \.smil manifest is an XML file that that acts as a wrapper for all of the files that are part of the asset\. The \.smil manifest lets MediaPackage know which MP4s are part of a single asset\.

**Resources**
+ For an example about how to create a \.smil manifest, see [\.smil using AWS Elemental MediaPackage VOD](https://aws.amazon.com/blogs/media/smil-using-aws-elemental-mediapackage-vod/) \(blog\)\.
+ For general information about Synchronized Multimedia Integration Language \(SMIL\), see the [SMIL 3\.0 specification](https://www.w3.org/TR/SMIL/)\.

MediaPackage supports the following attributes in a \.smil manifest\.

**Attributes**
+ `audioName` \- The name of the audio track, such as `English 2`\.
+ `includeAudio` \- A boolean value that sets whether or not to include the audio tracks\. If you don't specify an `includeAudio` value, all tracks default to `true` \.
+ `src` or `name` \- Either the name or the source of the text stream or video file relative to the manifest location\.
+ `subtitleName` \- The subtitle name, such as `English`\.
+ `systemLanguage` or `language` \- The system language, such as `eng`\.

**Example \.smil manifest**  
The following is an example of a `.smil` manifest\.   

```
<?xml version="1.0" encoding="utf-8"?>
<smil>
    <body>
        <alias value="Example"/>
        <switch>
            <video name="example_360.mp4" systemLanguage="eng" audioName="English,French,Spanish" includeAudio="false,true/>
            <video name="example_480.mp4" systemLanguage="eng" audioName="English 2" includeAudio="false"/>
            <textstream src="example_subs_eng.srt" systemLanguage="eng" subtitleName="English" includeAudio="false"/>
            <textstream src="example_subs_fra.srt" systemLanguage="fra" subtitleName="French" includeAudio="false"/>
            <textstream src="example_subs_spa.srt" systemLanguage="spa" subtitleName="Spanish" includeAudio="false"/>
    </switch>
</body>
</smil>
```