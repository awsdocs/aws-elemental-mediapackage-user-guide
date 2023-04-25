# Encryption fields<a name="cfigs-cmaf-encryption"></a>

Protect your content from unauthorized use through content encryption and digital rights management \(DRM\)\. AWS Elemental MediaPackage uses the [AWS Secure Packager and Encoder Key Exchange \(SPEKE\) API](https://aws.amazon.com/media/tech/speke-basics-secure-packager-encoder-key-exchange-api/) to facilitate content encryption and decryption by a DRM provider\. Using SPEKE, the DRM provider supplies encryption keys to MediaPackage through the SPEKE API\. The DRM provider also supplies licenses to supported media players for decryption\. For more information about how SPEKE is used with services and features running in the cloud, see [AWS cloud\-based architecture](https://docs.aws.amazon.com/speke/latest/documentation/what-is-speke.html#services-architecture) in the *Secure Packager and Encoder Key Exchange API Specification guide*\.

**Note**  
To encrypt content, you must have a DRM solution provider, and be set up to use encryption\. For information, see [Content encryption and DRM in AWS Elemental MediaPackage](using-encryption.md)\. 

To serve content with copyright protection, Select **Enable encryption** and complete the additional fields as follows:

1. For **System IDs**, enter unique identifiers for your streaming protocol and DRM system\. Provide up to two system IDs\. If you provide more than one system ID, enter one per line\. If you do not know your IDs, ask your DRM solution provider\.

1. For **URL**, enter the URL of the API Gateway proxy that you set up to talk to your key server\. The API Gateway proxy must reside in the same AWS Region as MediaPackage\.

   The following example shows a URL\. 

   ```
   https://1wm2dx1f33.execute-api.us-west-2.amazonaws.com/SpekeSample/copyProtection
   ```

1. \(Optional\) For **SPEKE version**, choose the SPEKE version that you'd like to use for encryption\. SPEKE Version 1\.0 is the legacy version that uses CPIX Version 2\.0, and supports single key encryption\. SPEKE Version 2\.0 uses CPIX Version 2\.3, and supports multiple key encryption\. For more information about using SPEKE with MediaPackage, see [Content encryption and DRM in MediaPackage](https://docs.aws.amazon.com/mediapackage/latest/ug/using-encryption.html)\. 

   If you select **SPEKE Version 2\.0**, then also choose a **Video encryption preset** and an **Audio encryption preset**\. The video and audio presets determine which content keys MediaPackage uses to encrypt the audio and video tracks in your stream\. For more information about these presets, see [SPEKE Version 2\.0 presets](drm-content-speke-v2-presets.md)\.

    When using SPEKE Version 2\.0, MediaPackage disables key rotation\.

1. \(Optional\) For **Constant initialization vector** enter a 128\-bit, 16\-byte hex value represented by a 32\-character string, to be used with the key for encrypting content\.

1. For **Role ARN**, enter the Amazon Resource Name \(ARN\) of the IAM role that provides you access to send your requests through API Gateway\. Get this from your DRM solution provider\.

   The following example shows a role ARN\. 

   ```
   arn:aws:iam::444455556666:role/SpekeAccess
   ```