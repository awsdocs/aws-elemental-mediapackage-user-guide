# Choosing the right SPEKE Version<a name="encryption-choosing-speke-version"></a>

[SPEKE Version 1](https://docs.aws.amazon.com/speke/latest/documentation/the-speke-api.html) supports the use of a single encryption key for all audio and video tracks, and uses [CPIX Version 2\.0](https://dashif.org/docs/DASH-IF-CPIX-v2-0.pdf)\. For audio and video tracks, [SPEKE Version 2\.0](https://docs.aws.amazon.com/speke/latest/documentation/the-speke-api-v2.html) supports the use of multiple, distinct encryption keys and uses [CPIX Version 2\.3](https://dashif.org/docs/CPIX2.3/Cpix.html)\. For more information about SPEKE Version 2\.0 encryption configurations, see [SPEKE Version 2\.0 presets](drm-content-speke-v2-presets.md)\.

If multiple key encryption, or Content Protection Information Exchange \(CPIX\) Version 2\.3, are mandatory requirements for your content delivery, then SPEKE Version 2\.0 is a good choice\. However, SPEKE Version 2\.0 support is progressive across endpoint types in MediaPackage\. This means that some live options, like key rotation, aren't available yet\. Take these constraints in consideration when crafting your SPEKE integration strategy\. To learn more about the SPEKE Version 2\.0 roadmap for MediaPackage, contact your AWS account team\.

**Supported protocols and DRM platforms**

The following tables list the different protocols and digital rights management \(DRM\) platforms that SPEKE Version 1\.0 and SPEKE Version 2\.0 support\.


|  |  |  |  |  | 
| --- |--- |--- |--- |--- |
| SPEKE Version 1\.0 – Support matrix for protocol and DRM system | Microsoft PlayReady | Google Widevine | Apple FairPlay | AES\-128 | 
| Live | 
| Apple HLS |   |   |  √  Has key rotation  |  √   Has key rotation  | 
| CMAF Apple HLS |   |  √   Has key rotation  |  √   Has key rotation  |   | 
| DASH |  √   Has key rotation  |  √   Has key rotation  |   |   | 
| Microsoft Smooth | √ |   |   |   | 
| VOD | 
| Apple HLS |   |   | √ | √ | 
| CMAF Apple HLS |   | √ | √ |   | 
| DASH | √ | √ |   |   | 
| Microsoft Smooth | √ |   |   |   | 


|  |  |  |  |  | 
| --- |--- |--- |--- |--- |
| SPEKE Version 2\.0 – Support matrix for protocol and DRM system | Microsoft PlayReady | Google Widevine | Apple FairPlay | Irdeto Content Protection | 
| Live | 
| CMAF Apple HLS | √ | √ | √ |   | 
| DASH | √ | √ |   | √ | 
| VOD | 
| CMAF Apple HLS | √ | √ | √ |   | 
| DASH | √ | √ |   | √ | 