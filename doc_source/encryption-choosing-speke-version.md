# Choosing the right SPEKE version<a name="encryption-choosing-speke-version"></a>

[SPEKE v1](https://docs.aws.amazon.com/speke/latest/documentation/the-speke-api.html) supports the use of a single encryption key for all audio and video tracks, and uses [CPIX v2\.0](https://dashif.org/docs/DASH-IF-CPIX-v2-0.pdf)\. [SPEKE v2](https://docs.aws.amazon.com/speke/latest/documentation/the-speke-api-v2.html) supports the use of multiple, distinct encryption keys for audio and video tracks, and uses [CPIX v2\.3](https://dashif.org/docs/CPIX2.3/Cpix.html)\.

If multi\-key encryption or CPIX v2\.3 are mandatory requirements for your content delivery, then SPEKE v2 is likely the right choice for you\. However, SPEKE v2 support rollout is progressive across endpoint types in MediaPackage\. This means that some live options like key rotation aren't available yet\.Take these constraints in consideration when crafting your SPEKE integration strategy\. Reach out to your AWS account team to learn more about the SPEKE v2 roadmap for MediaPackage\.

**Supported protocols and DRM platforms**

The following tables list the different protocols and DRM platforms that SPEKE v1 and SPEKE v2 support:


|  |  |  |  |  | 
| --- |--- |--- |--- |--- |
| SPEKE v1 – Support matrix for protocol and DRM system | Microsoft PlayReady | Google Widevine | Apple FairPlay | AES\-128 | 
| Live | 
| Apple HLS |   |   |  √   with key rotation  |  √   with key rotation  | 
| CMAF Apple HLS |   |  √   with key rotation  |  √   with key rotation  |   | 
| DASH |  √   with key rotation  |  √   with key rotation  |   |   | 
| Microsoft Smooth | √ |   |   |   | 
| VOD | 
| Apple HLS |   |   | √ | √ | 
| CMAF Apple HLS |   | √ | √ |   | 
| DASH | √ | √ |   |   | 
| Microsoft Smooth | √ |   |   |   | 


|  |  |  |  | 
| --- |--- |--- |--- |
| SPEKE v2 – Support matrix for protocol and DRM system | Microsoft PlayReady | Google Widevine | Apple FairPlay | 
| Live | 
| CMAF Apple HLS | √ | √ | √ | 
| DASH | √  | √  |   | 