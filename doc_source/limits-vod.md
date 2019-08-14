# VOD Content Limits<a name="limits-vod"></a>

This section describes the limits for video on demand \(VOD\) content in AWS Elemental MediaPackage\. For information about requesting an increase to soft limits, see [AWS Service Limits](https://docs.aws.amazon.com/general/latest/gr/aws_service_limits.html)\. Hard limits can't be changed\.

## VOD Soft Limits<a name="soft-limits-vod"></a>

The following table describes limits in AWS Elemental MediaPackage for VOD content that can be increased\. For information about changing limits, see [AWS Service Limits](https://docs.aws.amazon.com/general/latest/gr/aws_service_limits.html)\. 

For some customers, your account limit might be below these published limits\. If you believe that you encountered a Resource limit exceeded error wrongfully, [create a Service Limit Increase](https://console.aws.amazon.com/support/v1#/case/create) case and provide details such as how many resources you have configured and what you were trying to do\.


| Resource | Default Limit | 
| --- | --- | 
| Maximum Packaging Groups | 10 Increasing your packaging group limit doesn't always mean that you also need to increase your assets or packaging configurations\. For example, if you need 14 groups and want to serve HLS, HLS encrypted, and DASH content from each asset, you need only 3 packaging configurations for each asset \(one for each output type\)\. You do need to increase your packaging group limit, but not the packaging configuration limit because you have fewer than 10 configurations per packaging group\.  | 
| Maximum Packaging Configurations per Packaging Group | 10This is a *per packaging group* limit\. Each packaging configuration represents the output package that you use\. If one packaging group has configurations for HLS, HLS encrypted, DASH, DASH encrypted, Microsoft Smooth, and Microsoft Smooth encrypted content, then that group has 6 packaging configurations and falls within the 10 configurations limit\. If you have 10 packaging groups set up this same way, then you still haven't exceeded the limit because each group uses only 6 configurations\. | 
| Maximum Assets per Packaging Group | 1000This is a *per packaging group* limit\. If you have 1100 assets spread out over multiple packaging groups, then you still haven't exceeded the limit if each group has no more than 1000 assets\. | 

## VOD Hard Limits<a name="hard-limits-vod"></a>

The following table describes limits within AWS Elemental MediaPackage for VOD content that can't be increased\.


| Resource or Operation | Limit | 
| --- | --- | 
| Input Stream Limits | 30 streams per asset, and 10 tracks per stream | 
| Request Rates per Asset |  200 output requests per second  | 
| REST API Requests |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/mediapackage/latest/ug/limits-vod.html)  | 