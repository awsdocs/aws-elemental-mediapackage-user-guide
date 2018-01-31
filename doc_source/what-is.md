# What Is AWS Elemental MediaPackage?<a name="what-is"></a>

AWS Elemental MediaPackage is a just\-in\-time video packaging and origination service that runs in the AWS Cloud\. With AWS Elemental MediaPackage, you can deliver highly secure, scalable, and reliable video streams to a wide variety of playback devices and content distribution networks \(CDNs\)\. 

AWS Elemental MediaPackage offers a broadcast\-grade viewing experience for viewers, while allowing you the flexibility to control and protect your content\. Additionally, the built\-in resiliency and scalability of AWS Elemental MediaPackage means that you have the right amount of resources at the right time, with no manual intervention required\.


+ [Are You a First\-Time User of AWS Elemental MediaPackage?](#first-time-user)
+ [Concepts and Terminology](what-is-terms.md)
+ [How AWS Elemental MediaPackage Works](what-is-flow.md)
+ [Features of AWS Elemental MediaPackage](what-is-features.md)
+ [Related Services](#related-services)
+ [Accessing AWS Elemental MediaPackage](#accessing-emp)
+ [Regions for AWS Elemental MediaPackage](#regions-and-endpoints)

## Are You a First\-Time User of AWS Elemental MediaPackage?<a name="first-time-user"></a>

If you are a first\-time user of AWS Elemental MediaPackage, we recommend that you begin by reading the following sections:

+ [How AWS Elemental MediaPackage Works](what-is-flow.md)

+ [Concepts and Terminology](what-is-terms.md)

+ [Features of AWS Elemental MediaPackage](what-is-features.md)

+ [Getting Started with AWS Elemental MediaPackage](getting-started.md)

## Related Services<a name="related-services"></a>

+ **Amazon CloudFront** is a global content delivery network \(CDN\) service that securely delivers data and videos to your viewers\. Use CloudFront to deliver content with the best possible performance\. For more information, see [Amazon CloudFront](https://aws.amazon.com/cloudfront/)\.

+ **Amazon CloudWatch** is a monitoring service for AWS Cloud resources and the applications that you run on AWS\. Use CloudWatch to track metrics such as ingress and egress request counts\. For more information, see [Amazon CloudWatch](https://aws.amazon.com/cloudwatch/)\.

+ **AWS Elemental MediaLive** is a live video processing service that encodes high\-quality live video streams for broadcast television and multi\-screen devices\. Use AWS Elemental MediaLive to encode content streams and send them to AWS Elemental MediaPackage for packaging\. For more information about how encoders \(such as AWS Elemental MediaLive\) work with AWS Elemental MediaPackage, see [How AWS Elemental MediaPackage Works](what-is-flow.md)\.

+ **AWS Identity and Access Management \(IAM\)** is a web service that helps you securely control access to AWS resources for your users\. Use IAM to control who can use your AWS resources \(authentication\) and what resources users can use in which ways \(authorization\)\. For more information, see [[ERROR] BAD/MISSING LINK TEXT](setting-up.md)\.

## Accessing AWS Elemental MediaPackage<a name="accessing-emp"></a>

You can access AWS Elemental MediaPackage through the console, AWS Command Line Interface \(AWS CLI\), or AWS Elemental MediaPackage REST API\. 

+ Console access: 

  ```
  https://<region>.console.aws.amazon.com/mediapackage/home
  ```

+ AWS CLI endpoint: 

  ```
  aws mediapackage
  ```

+ AWS Elemental MediaPackage REST API endpoint: 

  ```
  https://config.mediapackage.<region>.amazonaws.com
  ```

## Regions for AWS Elemental MediaPackage<a name="regions-and-endpoints"></a>

AWS Elemental MediaPackage is available in the following regions:

+ US East \(N\. Virginia\)

+ US West \(Oregon\)

+ Asia Pacific \(Singapore\)

+ Asia Pacific \(Sydney\)

+ Asia Pacific \(Tokyo\)

+ EU \(Ireland\)