# Document History for User Guide<a name="doc-history"></a>

The following table describes important changes in each release of the *AWS Elemental MediaPackage User Guide* after May 2018\. For notification about updates to this documentation, you can subscribe to an RSS feed\.
+ **API version:** 1\.0
+ **Latest documentation update:** November 14, 2018

| Change | Description | Date | 
| --- |--- |--- |
| [Updated content retention window limit\.](limits.md#hard-limits) | AWS Elemental MediaPackage now retains content for 336 hours \(14 days\)\. | November 13, 2018 | 
| [Added content key encryption to DRM encryption](using-encryption.md#drm-content-key-encryption) | Added the option to encrypt content keys\. Prior to this, AWS Elemental MediaPackage supported clear key delivery only\. To use content key encryption, your DRM key provider must support encrypted content keys\. If you enable this feature for a key provider that doesn't handle content key encryption, the operation fails\. | November 8, 2018 | 
| [Added input redundancy information\.](what-is-flow-ir.md) | Added *How Input Redundancy Works* topic to discuss how you can ingress two identical streams with AWS Elemental MediaPackage\. | August 28, 2018 | 
| [Added Amazon CloudFront console integration information\.](cdns.md) | Added sections about working with distributions in CloudFront, including how to create a distribution from the AWS Elemental MediaPackage console\. | August 3, 2018 | 
| [Added information about multi\-period DASH\.](multi-period.md) | Added *Multi\-period DASH in AWS Elemental MediaPackage* topic to discuss the purpose and functionality of multiple periods in DASH manifests\. | July 18, 2018 | 
| [Added content delivery network \(CDN\) information\.](cdns.md) | Added *Working with CDNs* topic to discuss how AWS Elemental MediaPackage works with CDNs such as Amazon CloudFront\. | May 31, 2018 | 

## Earlier Updates<a name="earlier-updates"></a>

The following table describes important changes in each release of the *AWS Elemental MediaPackage User Guide* before May 2018\.


****  

| Change | Description | Date | 
| --- | --- | --- | 
| Initial document creation\. | New document\. | November 27, 2017 | 
| Corrected links and added whitelisting\. | Corrected links to the AWS Elemental MediaPackage console and AWS Elemental MediaPackage API Reference\.In Working with Endpoints, added reference to access control fields\. | December 1, 2017 | 
| Added IAM policy information specific to AWS Elemental MediaPackage\. | In [Setting Up AWS Elemental MediaPackage](setting-up.md), added instructions for creating non\-admin roles with limited permissions\. | December 13, 2017 | 
| Added hard limit information\. | In [Limits in AWS Elemental MediaPackage](limits.md), added information about limits that can't be changed \(hard limits\)\. | December 20, 2017 | 
| Updated IAM policy information\. | In [Setting Up AWS Elemental MediaPackage](setting-up.md), added information about policies specific to AWS Elemental MediaPackage\. | January 5, 2018 | 
| Added Amazon CloudWatch Events information\. | Added [Monitoring AWS Elemental MediaPackage with Amazon CloudWatch Events](monitoring-cloudwatch-events.md) section about the CloudWatch Events that AWS Elemental MediaPackage supports\. | February 14, 2018 | 
| Added CMAF endpoint information\. | Added [Creating a Common Media Application Format \(CMAF\) Endpoint](endpoints-cmaf.md) section for new output type\. | April 6, 2018 | 
| Updated feature functionality\. | In [Features of AWS Elemental MediaPackage](what-is-features.md), added feature support for HDR\-10\. | April 30, 2018 | 
| Added content delivery network \(CDN\) information\. | Added topic [Working with Content Delivery Networks \(CDNs\)](cdns.md) to discuss how AWS Elemental MediaPackage works with CDNs such as Amazon CloudFront\. | May 31, 2018 | 

**Note**  
The AWS Media Services are not designed or intended for use with applications or in situations requiring fail‐safe performance, such as life safety operations, navigation or communication systems, air traffic control, or life support machines in which the unavailability, interruption or failure of the services could lead to death, personal injury, property damage or environmental damage\.