# Creating a SMIL file<a name="supported-inputs-vod-smil"></a>

When you send an VOD MP4 asset to AWS Elemental MediaPackage, you have to include a Synchronized Multimedia Integration Language \(SMIL\) file as well\. This `.smil` file acts as a wrapper for all of the files that are part of the asset\. 

MediaPackage supports the following tags attributes in a `.smil` file\.

**Attributes**
+ `audioName`
+ `src` or `name`
+ `subtitleName`
+ `systemLanguage` or `language`

**Example Supported SMIL structure**  
The following is an example of a `.smil` manifest\.   

```
<?xml version="1.0" encoding="utf-8"?>
<smil>
    <body>
        <alias value="Example"/>
        <switch>
            <video name="example_360.mp4" systemLanguage="eng" audioName="English,French,Spanish"/>
            <video name="example_480.mp4" systemLanguage="eng" audioName="English 2"/>
            <textstream src="example_subs_eng.srt" systemLanguage="eng" subtitleName="English"/>
            <textstream src="example_subs_fra.srt" systemLanguage="fra" subtitleName="French"/>
            <textstream src="example_subs_spa.srt" systemLanguage="spa" subtitleName="Spanish"/>
    </switch>
</body>
</smil>
```