# AWS Elemental MediaPackage Events<a name="cloudwatch-events-example"></a>

AWS Elemental MediaPackage integrates with Amazon CloudWatch Events to notify you of certain events that affect your channels and endpoints\. Each event is represented in [JSON \(JavaScript Object Notation\)](http://json.org) and contains the event name, the date and time when the event occurred, the channel or endpoint affected, and more\. You can use CloudWatch Events to collect these events and set up rules that route them to one or more *targets* such as AWS Lambda functions, Amazon SNS topics, Amazon SQS queues, streams in Amazon Kinesis Data Streams, or built\-in targets\.

For more information about using CloudWatch Events with other kinds of events, see the [Amazon CloudWatch Events User Guide](http://docs.aws.amazon.com/AmazonCloudWatch/latest/events/)\.

The following topics describe the CloudWatch Events that AWS Elemental MediaPackage creates\.

**Topics**
+ [Input State Events](#input-state-events)
+ [Key Provider State Events](#key-provider-state-events)

## Input State Events<a name="input-state-events"></a>

A channel in AWS Elemental MediaPackage has exceeded the limit for the number of input streams\. For information about limits, see [Limits in AWS Elemental MediaPackage](limits.md)\.

```
{
   "id": "7bf73129-1428-4cd3-a780-95db273d1602",
   "detail-type": "MediaPackage Input State",
   "source": "aws.mediapackage",
   "account": "aws_account_id",
   "time": "2015-11-11T21:29:54Z",
   "region": "us-west-2",
   "resources":[
      "arn:aws:mediapackage:us-west-2:aws_account_id:channels/262ff182d46d4b399fcabea1364df682"
   ],
   "detail":{
      "event": "MaxIngestStreamsError",
      "message": "Parent Manifest [%s] has [23] streams, more than [20] allowed: (index_1.m3u8,index_2.m3u8,index_3.m3u8,index_4.m3u8,index_5.m3u8,index_6.m3u8,index_7.m3u8,index_8.m3u8,index_9.m3u8,index_10.m3u8,index_11.m3u8,index_12.m3u8,index_13.m3u8,index_14.m3u8,index_15.m3u8,index_16.m3u8,index_17.m3u8,index_18.m3u8,index_19.m3u8,index_20.m3u8,index_21.m3u8,index_22.m3u8,index_23.m3u8)"
   }
}
```

## Key Provider State Events<a name="key-provider-state-events"></a>

When you're using content encryption on an endpoint, AWS Elemental MediaPackage can't reach the key provider\. For information about DRM and encryption, see [http://docs.aws.amazon.com/speke/latest/documentation/](http://docs.aws.amazon.com/speke/latest/documentation/)\.

```
{
   "id": "7bf73129-1428-4cd3-a780-98ds273d1602",
   "detail-type": "MediaPackage Key Provider State",
   "source": "aws.mediapackage",
   "account": "aws_account_id",
   "time": "2015-11-11T21:29:54Z",
   "region": "us-west-2",
   "resources":[
      "arn:aws:mediapackage:us-west-2:aws_account_id:origin_endpoints/70b44e2e666c4bdc9e5f4488e1f1aa99"
   ],
   "detail":{
      "event": "KeyProviderError",
      "message": "message-text"
   }
}
```