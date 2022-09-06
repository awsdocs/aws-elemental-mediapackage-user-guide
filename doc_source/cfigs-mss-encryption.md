# Encryption fields<a name="cfigs-mss-encryption"></a>

Protect your content from unauthorized use through content encryption and digital rights management \(DRM\)\. AWS Elemental MediaPackage uses the [AWS Secure Packager and Encoder Key Exchange \(SPEKE\) API](https://aws.amazon.com/media/tech/speke-basics-secure-packager-encoder-key-exchange-api/) to facilitate content encryption and decryption by a DRM provider\. Using SPEKE, the DRM provider supplies encryption keys to AWS Elemental MediaPackage through the SPEKE API\. The DRM provider also supplies licenses to supported media players for decryption\. For more information about how SPEKE is used with services and features running in the cloud, see [AWS cloud\-based architecture](https://docs.aws.amazon.com/speke/latest/documentation/what-is-speke.html#services-architecture) in the *Secure Packager and Encoder Key Exchange API Specification guide*\.

**Note**  
To encrypt content, you must have a DRM solution provider, and be set up to use encryption\. For information, see [Content encryption and DRM in AWS Elemental MediaPackage](using-encryption.md)\. 

To serve content with copyright protection, choose **Enable encryption ** and complete the additional fields as follows:

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

1. For **System IDs**, enter unique identifiers for your streaming protocol and DRM system\. Provide up to three IDs for CMAF, two IDs for DASH, and exactly one for the other streaming protocols\. If you provide more than one system ID, enter one per line and choose **Add**\. For a list of common system IDs, see [DASH\-IF System IDs](https://dashif.org/identifiers/content_protection/)\. If you do not know your IDs, ask your DRM solution provider\.