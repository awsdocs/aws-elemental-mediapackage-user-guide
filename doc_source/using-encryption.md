# Using Encryption in AWS Elemental MediaPackage<a name="using-encryption"></a>

Protect your content from unauthorized use through encryption\. Digital rights management \(DRM\) systems provide keys to AWS Elemental MediaPackage for content encryption, and licenses to supported players and other consumers for decryption\.

**Note**  
To encrypt content, you must have a DRM solution provider\.   
For an overview, see [https://docs\.aws\.amazon\.com/speke/latest/documentation/what\-is\-speke\.html\#services\-architecture](https://docs.aws.amazon.com/speke/latest/documentation/what-is-speke.html#services-architecture)\.
To get set up, see [https://docs\.aws\.amazon\.com/speke/latest/documentation/customer\-onboarding\.html](https://docs.aws.amazon.com/speke/latest/documentation/customer-onboarding.html)\.

Your DRM solution provider can help you get set up to use DRM encryption in AWS Elemental MediaPackage\. 

## Using Encrypted Content Keys with DRM<a name="drm-content-key-encryption"></a>

For the most secure DRM encryption solution, use encrypted content keys in addition to encrypted content\. To use encrypted content keys, you must import suitable certificates into the AWS Certificate Manager\. For information about ACM, see the [AWS Certificate Manager User Guide](https://docs.aws.amazon.com/acm/latest/userguide/)\. 

Run AWS Certificate Manager in the same Region as you run AWS Elemental MediaPackage\.

**To prepare a certificate for DRM content key encryption**

1. Obtain a 2048 RSA, SHA\-512\-signed certificate\. 

1. Open the ACM console at [https://console\.aws\.amazon\.com/acm/](https://console.aws.amazon.com/acm/)\.

1. Import the certificate into ACM according to the instructions at [Importing Certificates into AWS Certificate Manager](https://docs.aws.amazon.com/acm/latest/userguide//import-certificate.html)\. Note the resulting certificate ARN because you will need it later\.

   For use in DRM encryption, your certificate must have a status of **Issued** in ACM\.

**To use a certificate in AWS Elemental MediaPackage**

When you use DRM encryption in your endpoint configuration, provide your certificate ARN in the encryption parameters\. This enables content key encryption\. You can use the same certificate ARN for multiple events\. For information, see the encryption settings information in [Working with Endpoints in AWS Elemental MediaPackage](endpoints.md)\. 

**To renew a certificate**

To renew a certificate that you are using in AWS Elemental MediaPackage, reimport it in AWS Certificate Manager\. The certificate renews without any disruption of its use in MediaPackage\. 

**To delete a certificate**

To delete a certificate from AWS Certificate Manager, it must not be associated with any other service\. Delete the certificate ARN from endpoint configurations where you have used it, then delete it from ACM\. 

**Note**  
If you delete a certificate ARN from an active endpoint, the endpoint keeps running, but stops using content key encryption\. 