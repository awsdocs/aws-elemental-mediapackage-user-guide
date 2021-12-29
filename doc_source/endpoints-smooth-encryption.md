# Encryption fields<a name="endpoints-smooth-encryption"></a>

Protect your content from unauthorized use through content encryption and digital rights management \(DRM\)\. AWS Elemental MediaPackage uses the [AWS Secure Package and Encoder Key Exchange \(SPEKE\) API](https://aws.amazon.com/media/tech/speke-basics-secure-packager-encoder-key-exchange-api/) to facilitate content encryption and decryption by a DRM provider\. Using SPEKE, the DRM provider supplies encryption keys to AWS Elemental MediaPackage through the SPEKE API\. The DRM provider also supplies licenses to supported media players for decryption\. For more information about how SPEKE is used with services and features running in the cloud, see [AWS cloud\-based architecture](https://docs.aws.amazon.com/speke/latest/documentation/what-is-speke.html#services-architecture) in the *Secure Packager and Encoder Key Exchange API Specification guide*\.

**Note**  
To encrypt content, you must have a DRM solution provider and be set up to use encryption\. For information, see [Content encryption and DRM in AWS Elemental MediaPackage](using-encryption.md)\. 

1. To serve content without copyright protection, keep **No encryption** selected\.

1. To serve content with copyright protection, choose **Encrypt content** and complete the additional fields as follows:

   1. For **Resource ID**, enter an identifier for the content\. The service sends this to the key server to identify the current endpoint\. How unique you make this depends on how fine\-grained you want access controls to be\. The service does not allow you to use the same ID for two simultaneous encryption processes\. The resource ID is also known as the content ID\. 

      The following example shows a resource ID\.

      ```
      MovieNight20171126093045
      ```

   1. For **System IDs**, enter unique identifiers for your streaming protocol and DRM system\. Provide up to one system ID\. If you do not know your ID, ask your DRM solution provider\.

   1. For **URL**, enter the URL of the API Gateway proxy that you set up to talk to your key server\. The API Gateway proxy must reside in the same AWS Region as MediaPackage\.

      The following example shows a URL\. 

      ```
      https://1wm2dx1f33.execute-api.us-west-2.amazonaws.com/SpekeSample/copyProtection
      ```

   1. For **Role ARN**, enter the Amazon Resource Name \(ARN\) of the IAM role that provides you access to send your requests through API Gateway\. Get this from your DRM solution provider\.

      The following example shows a role ARN\. 

      ```
      arn:aws:iam::444455556666:role/SpekeAccess
      ```

   1. **Certificate ARN** – \(Optional\) Enter a 2048 RSA certificate ARN to use for content key encryption\. Use this option only if your DRM key provider supports content key encryption\. If you use this and your key provider doesn't support it, the event fails\.

      To enter a certificate ARN here, you must have already imported the corresponding certificate into AWS Certificate Manager\. Then enter the certificate ARN from ACM here\. 

      For information about key encryption, see [Preparing and managing certificates for use with content keys](drm-content-key-encryption.md)\.