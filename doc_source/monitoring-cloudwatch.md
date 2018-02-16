# Monitoring AWS Elemental MediaPackage with Amazon CloudWatch<a name="monitoring-cloudwatch"></a>

You can monitor AWS Elemental MediaPackage using CloudWatch, which collects raw data and processes it into readable, near real\-time metrics\. These statistics are kept for 15 months, so that you can access historical information and gain a better perspective on how your web application or service is performing\. You can also set alarms that watch for certain thresholds, and send notifications or take actions when those thresholds are met\. For more information, see the [Amazon CloudWatch User Guide](http://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/)\.

**To view metrics using the AWS Elemental MediaPackage console**  
AWS Elemental MediaPackage displays metrics throughout the console\.

1. Open the AWS Elemental MediaPackage console at [https://console\.aws\.amazon\.com/mediapackage/](https://console.aws.amazon.com/mediapackage/)\.

1. Navigate to the appropriate page to view metrics:

   + For metrics on all channels and endpoints in the region, go to the **Channels** page\.

   + For metrics on a specific channel and all of its endpoints, go to the channel's details page\.

   + For metrics on a specific endpoint and its channel, go to the endpoint's details page\.

1. \(Optional\) To refine the metrics view, choose **Open in CloudWatch**\.

**To view metrics using the CloudWatch console**  
Metrics are grouped first by the service namespace, and then by the various dimension combinations within each namespace\.

1. Sign in to the AWS Management Console and open the CloudWatch console at [https://console\.aws\.amazon\.com/cloudwatch/](https://console.aws.amazon.com/cloudwatch/)\.

1. In the navigation pane, choose **Metrics**\.

1. Under **All metrics**, choose the **AWS/MediaPackage** namespace\.

1. Choose the metric dimension to view the metrics \(for example, choose `channel` to view metrics per channel\)\.

**To view metrics using the AWS CLI**  
At a command prompt, use the following command:

```
aws cloudwatch list-metrics --namespace "AWS/MediaPackage"
```

## AWS Elemental MediaPackage CloudWatch Metrics<a name="metrics"></a>

The `AWS/MediaPackage` namespace includes the following metrics\. AWS Elemental MediaPackage publishes metrics to CloudWatch every minute, if not sooner\.


| Metric | Description | 
| --- | --- | 
|  EgressBytes  | Number of bytes that AWS Elemental MediaPackage successfully outputs for each request\. If AWS Elemental MediaPackage doesn't receive any requests for egress in the specified interval, then no data is given\.Units: BytesValid statistics:[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/mediapackage/latest/ug/monitoring-cloudwatch.html)Valid dimensions: [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/mediapackage/latest/ug/monitoring-cloudwatch.html) | 
|  EgressRequestCount  | Number of content requests that AWS Elemental MediaPackage receives\. If AWS Elemental MediaPackage doesn't receive any requests for egress in the specified interval, then no data is given\.Units: CountValid statistics:[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/mediapackage/latest/ug/monitoring-cloudwatch.html)Valid dimensions: [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/mediapackage/latest/ug/monitoring-cloudwatch.html) | 
|  EgressResponseTime  | The time that it takes AWS Elemental MediaPackage to process each egress request\. If AWS Elemental MediaPackage doesn't receive any requests for egress in the specified interval, then no data is given\.Units: MillisecondsValid statistics:[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/mediapackage/latest/ug/monitoring-cloudwatch.html)Valid dimensions: [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/mediapackage/latest/ug/monitoring-cloudwatch.html) | 
|  IngressBytes  | Number of bytes that AWS Elemental MediaPackage ingests for each request\. If AWS Elemental MediaPackage doesn't receive any requests for egress in the specified interval, then no data is given\.Units: BytesValid statistics:[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/mediapackage/latest/ug/monitoring-cloudwatch.html)Valid dimensions: [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/mediapackage/latest/ug/monitoring-cloudwatch.html) | 
|  IngressResponseTime  | The time that it takes AWS Elemental MediaPackage to process each ingest request\. If AWS Elemental MediaPackage doesn't receive any requests for egress in the specified interval, then no data is given\.Units: MillisecondsValid statistics:[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/mediapackage/latest/ug/monitoring-cloudwatch.html)Valid dimensions: [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/mediapackage/latest/ug/monitoring-cloudwatch.html) | 

## AWS Elemental MediaPackage CloudWatch Dimensions<a name="dimensions"></a>

You can filter the `AWS/MediaPackage` data using the following dimensions\.


| Dimension | Description | 
| --- | --- | 
|  No Dimension  | Metrics are aggregated and shown for all channels, endpoints, or status codes\. | 
|  `Channel`  |  Metrics are shown only for the specified channel\. Value: The auto\-generated GUID of the channel\. Can be used alone or with other dimensions:  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/mediapackage/latest/ug/monitoring-cloudwatch.html)  | 
|  `OriginEndpoint`  |  Metrics are shown for the specified channel and endpoint combination\. Value: The auto\-generated GUID of the endpoint\. Must be used in conjunction with the `channel` dimension\.   | 
|  `StatusCodeRange`  |  Metrics are shown for the specified status code range\.  Value: `2xx`, `3xx`, `4xx`, or `5xx`\. Can be used alone or with other dimensions: [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/mediapackage/latest/ug/monitoring-cloudwatch.html)  | 