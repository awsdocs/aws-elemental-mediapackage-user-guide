# Limits in AWS Elemental MediaPackage<a name="limits"></a>

The following sections provide information about the limits in AWS Elemental MediaPackage\. For information about requesting an increase to soft limits, see [AWS Service Limits](https://docs.aws.amazon.com/general/latest/gr/aws_service_limits.html)\. Hard limits cannot be changed\.

## Soft Limits<a name="soft-limits"></a>

The following table describes limits in AWS Elemental MediaPackage that can be increased\. For information about changing limits, see [AWS Service Limits](https://docs.aws.amazon.com/general/latest/gr/aws_service_limits.html)\. 


| Resource | Default Limit | 
| --- | --- | 
| Maximum Channels | 10 Increasing your channel limit doesn't always mean that you also need to increase your endpoints\. For example, if you need 14 channels and want to serve HLS, HLS encrypted, and DASH content from each channel, you need only three endpoints for each channel \(one for each output type\)\. The default endpoint limit is 10 so, although you do need a channel limit increase, you don't need to increase your endpoint limit\. You won't exceed the limit of 10 endpoints *per channel*\.  | 
| Maximum Endpoints per Channel | 10This is a *per channel* limit\. Each endpoint represents the output package that you use\. If one channel serves HLS, HLS encrypted, DASH, DASH encrypted, Microsoft Smooth, and Microsoft Smooth encrypted content, then that channel has six endpoints and falls within the 10 endpoints limit\. If you have 10 channels set up this same way, then you still haven't exceeded the limit because each channel uses only 6 endpoints\. | 

## Hard Limits<a name="hard-limits"></a>

The following table describes limits within AWS Elemental MediaPackage that can't be increased\.


| Resource or Operation | Limit | 
| --- | --- | 
| Ingest Stream Limits | 20 streams per channel, and 10 tracks per stream | 
| Maximum Content Retention | 336 hours \(14 days\) | 
| Maximum Live Manifest Length | 5 minutes | 
| Maximum Time\-shifted Manifest Length | 6 hours | 
| Request Rates per Channel |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/mediapackage/latest/ug/limits.html)  | 
| REST API Requests |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/mediapackage/latest/ug/limits.html)  | 