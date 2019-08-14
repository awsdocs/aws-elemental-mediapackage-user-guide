# Live Content Limits<a name="limits-live"></a>

This section describes the limits for live content in AWS Elemental MediaPackage\. For information about requesting an increase to soft limits, see [AWS Service Limits](https://docs.aws.amazon.com/general/latest/gr/aws_service_limits.html)\. Hard limits can't be changed\.

## Live Soft Limits<a name="soft-limits"></a>

The following table describes limits in AWS Elemental MediaPackage for live content that can be increased\. For information about changing limits, see [AWS Service Limits](https://docs.aws.amazon.com/general/latest/gr/aws_service_limits.html)\. 

For some customers, your account limit might be below these published limits\. If you believe that you encountered a Resource limit exceeded error wrongfully, [create a Service Limit Increase](https://console.aws.amazon.com/support/v1#/case/create) case and provide details such as how many channels or endpoints you have and what you were trying to do\.


| Resource | Default Limit | 
| --- | --- | 
| Maximum Channels | 30 Increasing your channel limit doesn't always mean that you also need to increase your endpoints\. For example, if you need 34 channels and want to serve HLS, HLS encrypted, and DASH content from each channel, you need only 3 endpoints for each channel \(one for each output type\)\. The default endpoint limit is 10 so, although you do need a channel limit increase, you don't need to increase your endpoint limit\. You won't exceed the limit of 10 endpoints *per channel*\.  | 
| Maximum Endpoints per Channel | 10This is a *per channel* limit\. Each endpoint represents the output package that you use\. If one channel serves HLS, HLS encrypted, DASH, DASH encrypted, Microsoft Smooth, and Microsoft Smooth encrypted content, then that channel has 6 endpoints and falls within the 10 endpoints limit\. If you have 10 channels set up this same way, then you still haven't exceeded the limit because each channel uses only 6 endpoints\. | 

## Live Hard Limits<a name="hard-limits"></a>

The following table describes limits in AWS Elemental MediaPackage for live content that can't be increased\.


| Resource or Operation | Limit | 
| --- | --- | 
| Input Stream Limits | 30 streams per channel, and 10 tracks per stream | 
| Maximum Content Age for Time\-shifted Viewing | 336 hours \(14 days\) | 
| Maximum Live Manifest Length | 5 minutes | 
| Maximum Time\-shifted Manifest Length | 9 hours | 
| Request Rates per Channel |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/mediapackage/latest/ug/limits-live.html)  | 
| REST API Requests |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/mediapackage/latest/ug/limits-live.html)  | 