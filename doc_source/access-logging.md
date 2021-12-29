# Access logging<a name="access-logging"></a>

MediaPackage provides access logs that capture detailed information about requests sent to your MediaPackage channel or packaging group\. MediaPackage generates *ingress access logs* for requests sent to the channel's input endpoints, and *egress access logs* for requests sent to your channel's endpoints or packaging group's assets\. Each log contains information such as the time the request was received, the client's IP address, latencies, request paths, and server responses\. You can use these access logs to analyze service performance and troubleshoot issues\. They can also help you learn about your customer base and understand your MediaPackage bill\.

 Access logging is an optional feature of MediaPackage that is disabled by default\. After you enable access logging, MediaPackage captures the logs and saves them to the CloudWatch log group that you specify when you create or manage access logging\. Typical CloudWatch Logs charges apply\. 

**Topics**
+ [Permissions to publish access logs to CloudWatch](#permissions)
+ [Enable access logging](#enable-access-logging)
+ [Disable access logging](#disable-access-logging)
+ [Access log format](#access-log-format)
+ [Read the access logs](#read-access-logs)

## Permissions to publish access logs to CloudWatch<a name="permissions"></a>

When you enable access logging, MediaPackage creates an IAM service\-linked role, `AWSServiceRoleForMediaPackage`, in your AWS account\. This role allows MediaPackage to publish access logs to CloudWatch\. For information about how MediaPackage uses service\-linked roles, see [Using Service\-Linked Roles for MediaPackage](using-service-linked-roles.md)\.

## Enable access logging<a name="enable-access-logging"></a>

You can enable access logs using the AWS Management Console or the AWS CLI\.

**To enable access logs for an existing channel using the console**

1. Open the MediaPackage console at [https://console\.aws\.amazon\.com/mediapackage/](https://console.aws.amazon.com/mediapackage/)\.

1. Select your channel\.

1. In the **Configure Access Logs** section, do the following:

   1. Choose **Enable ingress access logs** or **Enable egress access logs**, or both\.

   1. You can specify a custom CloudWatch **Log group name**\. If left blank, the default group is used\.

**To enable access logs for an existing packaging group using the console**

1. Open the MediaPackage console at [https://console\.aws\.amazon\.com/mediapackage/](https://console.aws.amazon.com/mediapackage/)\.

1. Select **Packaging groups** from the navigation section\.

1. Choose your packaging group\.

   1. Select **Edit** in the navigation bar\.

   1. In the **Access logging** section, select **Enable egress access logs**\.

   1. You can specify a custom CloudWatch **Log group name**\. If left blank, the default group is used\.

1. Choose **Save changes**\.

**To enable access logs for a channel using the AWS CLI**  
Use the [configure\-logs](https://docs.aws.amazon.com/cli/latest/reference/mediapackage/configure-logs.html) command with the `--ingress-access-logs` parameter, `--egress-access-logs` parameter, or both, to enable access logging\. You can include a CloudWatch log group name for the `--ingress-access-logs` and `--egress-access-logs` parameters\. If you don't specify a log group name, then the MediaPackage default log group is used\. For ingress logs, the default log group is `/aws/MediaPackage/IngressAccessLogs`, and for egress logs the default log group is `/aws/MediaPackage/EgressAccessLogs`\.

Use the following command to enable both ingress and access logs using the default log groups:

```
aws mediapackage configure-logs --id channel-name --ingress-access-logs {} --egress-access-logs {}
```

This command has no return value\.

**To enable access logs for a packaging group using the AWS CLI**  
Use the [configure\-logs](https://docs.aws.amazon.com/cli/latest/reference/mediapackage-vod/configure-logs.html) command with the `--egress-access-logs` parameter to enable access logging\. You can include a CloudWatch log group name for the `--egress-access-logs` parameter\. If you don't specify a log group name, then the MediaPackage default log group is used\. For ingress logs, the default log group is `/aws/MediaPackage/IngressAccessLogs`, and for egress logs the default log group is `/aws/MediaPackage/EgressAccessLogs`\.

Use the following command to enable egress access logs using the default log groups:

```
aws mediapackage configure-logs --id package-name --egress-access-logs {}
```

This command has no return value\.

## Disable access logging<a name="disable-access-logging"></a>

You can disable access logs for your MediaPackage channel or packaging group at any time\.

**To disable access logging using the console**

1. Open the MediaPackage console at [https://console\.aws\.amazon\.com/mediapackage/](https://console.aws.amazon.com/mediapackage/)\.

   Select your channel or package group\.

1. Choose **Edit**\.

1. In the **Access logging** section, deselect **Ingress access logging**, **Egress access logging**, or both\.

1. Choose **Save changes**\.

**To disable access logging for a channel using the AWS CLI**  
Use the `configure-logs` command to disable access logging\. If one or more of the access log parameters aren't declared with the `configure-logs` command, then the corresponding access logs are disabled\. For example, in the following command egress access logs are enabled for a channel, and ingress access logs are disabled:

```
aws mediapackage configure-logs --id channel-name --egress-access-logs {}
```

This command has no return value\.

**To disable access logging for a packaging group using the AWS CLI**  
Use the `configure-logs` command to disable access logging\. If one or more of the access log parameters aren't declared with the `configure-logs` command, then the corresponding access logs are disabled\. For example, in the following command `configure-logs` doesn't include `--egress-access-logs` so egress logs are disabled:

```
aws mediapackage configure-logs --id package-group-name
```

This command has no return value\.

## Access log format<a name="access-log-format"></a>

The access log files consist of a sequence of JSON\-formatted log records, where each log record represents one request\. The order of the fields within the log can vary\. The following is an example channel egress access log:

```
{
    "timestamp": "2020-07-13T18:59:56.293656Z",
    "clientIp": "192.0.2.0/24",
    "processingTime": 0.445,
    "statusCode": "200",
    "receivedBytes": 468,
    "sentBytes": 2587370,
    "method": "GET",
    "request": "https://aaabbbcccdddee.mediapackage.us-east-1.amazonaws.com:443/out/v1/75ee4f20e5df43e5821e5cb17ea19238/hls_7_145095.ts?m=1538005779",
    "protocol": "HTTP/1.1",
    "userAgent": "sabr/3.0 Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US) AppleWebKit/528.18 (KHTML, like Gecko) Version/4.0 Safari/528.17",
    "account": "111122223333",
    "channelId": "my_channel",
    "channelArn": "arn:aws:mediapackage:us-west-2:111122223333:channels/ExampleChannelID",
    "domainName": "aaabbbcccdddee.mediapackage.us-east-1.amazonaws.com",
    "requestId": "aaaAAA111bbbBBB222cccCCC333dddDDD",
    "endpointId": "my_endpoint",
    "endpointArn": "arn:aws:mediapackage:us-west-2:111122223333:origin_endpoints/ExampleEndpointID"
}
```

The following list describes the log record fields, in order:

*timestamp*  
The time of day when the request was received\. The value is `ISO-8601` date time and is based on the system clock of the host that served the request\.

*clientIp*  
The IP address of the requesting client\.

*processingTime*  
The number of seconds that MediaPackage spent processing your request\. This value is measured from the time the last byte of your request was received until the time the first byte of the response was sent\.

*statusCode*  
The numeric HTTP status code of the response\.

*receivedBytes*  
The number of bytes in the request body that the MediaPackage server receives\.

*sentBytes*  
The number of bytes in the response body that the MediaPackage server sends\. This value often is the same as the value of the `Content-Length` header that's included with server responses\.

*method*  
The HTTP request method that was used for the request: DELETE, GET, HEAD, OPTIONS, PATCH, POST, or PUT\.

*request*  
The request URL\.

*protocol*  
The type of protocol used for the request, such as HTTP\.

*userAgent*  
A user\-agent string that identifies the client that originated the request, enclosed in double quotes\. The string consists of one or more product identifiers, product/version\. If the string is longer than 8 KB, it is truncated\.

*account*  
The AWS account ID of the account that was used to make the request\.

*channelId*  
The ID of the channel that received the request\.

*channelArn*  
The Amazon Resource Name \(ARN\) of the channel that received the request\.

*domainName*  
The server name indication domain provided by the client during the TLS handshake, enclosed in double quotes\. This value is set to `-` if the client doesn't support SNI or the domain doesn't match a certificate and the default certificate is presented to the client\.

*requestId*  
A string that is generated by MediaPackage to uniquely identify each request\.

*endpointId*  
The ID of the endpoint that received the request\.

*endpointArn*  
The Amazon Resource Name \(ARN\) of the endpoint that received the request\.

The order of the fields in the log can vary\.

## Read the access logs<a name="read-access-logs"></a>

MediaPackage writes the access logs to Amazon CloudWatch Logs\. Typical CloudWatch Logs charges apply\. Use CloudWatch Logs Insights to read the access logs\. For information on how to use CloudWatch Logs Insights, see [Analyzing Log Data with CloudWatch Logs Insights](https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/AnalyzingLogData.html) in the *AWS CloudWatch Logs User Guide*\.

**Note**  
The access logs can take a few minutes to appear in CloudWatch\. If you don't see the logs, wait a few minutes and try again\.

### Examples<a name="query-examples"></a>

 This section includes example queries that you can use to read MediaPackage debug log data\. 

**Example View the HTTP status code responses for a channel\.**  
 Use this query to view the responses by HTTP status code for a channel\. You can use this to view HTTP error code responses to help you to troubleshoot issues\.   

```
fields @timestamp, @message
| filter channelId like 'my-channel'
| stats count() by statusCode
```

**Example Get the number of requests per endpoint on a channel\.**  

```
fields @timestamp, @message
| filter channelId like 'my-channel'
| stats count() by endpointId
```

**Example View status codes per asset\.**  

```
fields @timestamp, @message
| filter assetArnlike 'my-asset-id'
| stats count() by statusCode
```

**Example Get the P99 response times for a packaging configuration over time**  

```
fields @timestamp, @message
| filter packagingConfigArn like 'my-dash-config'
| stats pct(processingTime, 99) by bin(5m)
```