# Live content quotas<a name="live-quotas"></a>

This section describes the quotas for live content in AWS Elemental MediaPackage\. For information about requesting an increase to soft quotas, see [AWS service quotas](https://docs.aws.amazon.com/general/latest/gr/aws_service_limits.html)\. Hard quotas can't be changed\.

## Live soft quotas<a name="live-soft-quotas"></a>

The following table describes quotas in AWS Elemental MediaPackage for live content that can be increased\. For information about changing quotas, see [AWS Service Quotas](https://docs.aws.amazon.com/general/latest/gr/aws_service_limits.html)\. 

For some customers, your account quota might be below these published quotas\. If you believe that you encountered a Resource limit exceeded error wrongfully, use the Service Quotas console to [request quota increases](https://console.aws.amazon.com/servicequotas/home?region=us-east-1#!/services/mediapackage/quotas)\.


| Resource | Default quota | 
| --- | --- | 
| Maximum Channels | 30 Increasing your channel quota doesn't always mean that you also need to increase your endpoints\. For example, if you need 34 channels and want to serve HLS, HLS encrypted, and DASH content from each channel, you need only 3 endpoints for each channel \(one for each output type\)\. The default endpoint quota is 10 so, although you do need a channel quota increase, you don't need to increase your endpoint quota\. You won't exceed the quota of 10 endpoints *per channel*\.  | 
| Maximum Endpoints per Channel | 10This is a *per channel* quota\. Each endpoint represents the output package that you use\. If one channel serves HLS, HLS encrypted, DASH, DASH encrypted, Microsoft Smooth, and Microsoft Smooth encrypted content, then that channel has 6 endpoints and falls within the 10 endpoints quota\. If you have 10 channels set up this same way, then you still haven't exceeded the quota because each channel uses only 6 endpoints\. | 
| Maximum Concurrent Harvest Jobs | 10 | 
| Maximum Live Manifest Length | 5 minutes | 

## Live hard quotas<a name="live-hard-quotas"></a>

The following table describes quotas in AWS Elemental MediaPackage for live content that can't be increased\.


| Resource or operation | Quota | 
| --- | --- | 
| Input Stream Quotas | 30 streams per channel, and 10 tracks per stream | 
| Maximum Content Age for Time\-shifted Viewing | 336 hours \(14 days\) | 
| Maximum Time\-shifted Manifest Length |   24 hours for all supported output formats: Apple HTTP Live Streaming \(HLS\), DASH\-ISO, Common Media Application Format \(CMAF\), and Microsoft Smooth Streaming \(MSS\)\.  | 
| Maximum Live\-to\-VOD Manifest Length |   24 hours for all supported output formats: Apple HTTP Live Streaming \(HLS\), DASH\-ISO, Common Media Application Format \(CMAF\), and Microsoft Smooth Streaming \(MSS\)\.  | 
| Request Rates per Channel |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/mediapackage/latest/ug/live-quotas.html)  | 
| REST API Requests |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/mediapackage/latest/ug/live-quotas.html)  | 