# Encryption Fields<a name="endpoints-smooth-encryption"></a>

Protect your content from unauthorized use through encryption\. Digital rights management \(DRM\) systems provide keys to MediaPackage for content encryption, and licenses to supported players for decryption\.

**Note**  
To encrypt content, you must have a DRM solution provider\. To get set up, see [http://docs\.aws\.amazon\.com/speke/latest/documentation/customer\-onboarding\.html](http://docs.aws.amazon.com/speke/latest/documentation/customer-onboarding.html)\.

1. To serve content without copyright protection, keep **No encryption** selected\.

1. To serve content with copyright protection, choose **Encrypt content** and complete the additional fields as follows:

   1. **Resource ID** – Identifier that you define for the content, which is sent to the key server to identify the current endpoint\. How unique you make this depends on how fine\-grained you want access controls to be\. The service does not allow you to use the same ID for two simultaneous encryption processes\. 

      The following example shows a resource ID:

      ```
      MovieNight20171126093045
      ```

   1. **System IDs** – Unique identifiers for your streaming protocol and DRM system\. Provide up to two IDs for DASH and exactly one for the other streaming protocols\. If you provide more than one system ID, enter them on separate lines, and do not separate them with commas or any other punctuation\. For a list of common system IDs, see [DASH\-IF System IDs](http://www.dashif.org/identifiers/protection/)\. If you do not know your IDs, ask your DRM solution provider\.

   1. **URL** – The URL from the API Gateway proxy that you set up to talk to your key server\. 

      The following example shows a URL: 

      ```
      https://1wm2dx1f33.execute-api.us-west-2.amazonaws.com/SpekeSample/copyProtection
      ```

   1. **Role ARN** – The Amazon Resource Name \(ARN\) of the IAM role that provides you access to send your requests through API Gateway\. Get this from your DRM solution provider\.

      The following example shows a role ARN: 

      ```
      arn:aws:iam::012345678901:role/SpekeAccess
      ```