# Content encryption and DRM in AWS Elemental MediaPackage<a name="using-encryption"></a>

Protect your content from unauthorized use through content encryption and digital rights management \(DRM\)\. AWS Elemental MediaPackage uses the [AWS Secure Packager and Encoder Key Exchange \(SPEKE\) API](https://aws.amazon.com/media/tech/speke-basics-secure-packager-encoder-key-exchange-api/) to facilitate content encryption and decryption by a DRM provider\. Using SPEKE, the DRM provider supplies encryption keys to MediaPackage through the SPEKE API\. The DRM provider also supplies licenses to supported media players for decryption\. For more information about how SPEKE is used with services and features running in the cloud, see [AWS cloud\-based architecture](https://docs.aws.amazon.com/speke/latest/documentation/what-is-speke.html#services-architecture) in the *Secure Packager and Encoder Key Exchange API Specification guide*\.

## Limitations and requirements<a name="encryption-requirements"></a>

When implementing content encryption for AWS Elemental MediaPackage, refer to the following limitations and requirements:
+ Use the AWS Secure Packager and Encoder Key Exchange \(SPEKE\) API to facilitate integration with a digital rights management \(DRM\) provider\. For information about SPEKE, see [What is Secure Packager and Encoder Key Exchange?](https://docs.aws.amazon.com/speke/latest/documentation/what-is-speke.html)
+ Your DRM provider must support SPEKE\. For a list of DRM providers that support SPEKE, see the [Get on board with a DRM platform provider](https://docs.aws.amazon.com/speke/latest/documentation/customer-onboarding.html#choose-drm-provider) topic in the *MediaPackage User Guide*\. Your DRM solution provider can help you set up DRM encryption use in AWS Elemental MediaPackage\.
+ Use MediaPackage to encrypt live and video on demand \(VOD\) content\. Assets that must be delivered through the MediaPackage VOD service must be harvested from an unencrypted HLS live endpoint\. You can harvest live\-to\-VOD assets from HLS and DASH endpoints that are protected by DRM or encryption\. However, the MediaPackage VOD service can't ingest these assets because they're encrypted \(not clear\) content\. For more information about this kind of workflow, see [Creating live\-to\-VOD assets with AWS Elemental MediaPackage](ltov.md)\.

The following sections provide guidance on how to choose and implement content encryption using SPEKE for MediaPackage\.

**Topics**
+ [Limitations and requirements](#encryption-requirements)
+ [Choosing the right SPEKE Version](encryption-choosing-speke-version.md)
+ [Deploying SPEKE](encryption-deploying-speke.md)
+ [Preparing and managing certificates for use with content keys](drm-content-key-encryption.md)
+ [Understanding key rotation behavior](drm-content-key-rotation.md)
+ [SPEKE Version 2\.0 presets](drm-content-speke-v2-presets.md)