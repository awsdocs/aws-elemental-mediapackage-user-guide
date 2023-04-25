# CDN authorization in AWS Elemental MediaPackage<a name="cdn-auth"></a>

*Content Delivery Network \(CDN\) authorization* helps you to protect your content from unauthorized use\. When you configure CDN authorization, MediaPackage only fulfills playback requests that are authorized between MediaPackage and your CDN\. This prevents users from bypassing the CDN in order to directly access your content on the origin\.

## How it works<a name="working-with-cdn-auth"></a>

You configure your CDN, such as Amazon CloudFront, to include a *custom HTTP header* in content requests to MediaPackage\.

Custom HTTP header and example value\.

```
X-MediaPackage-CDNIdentifier: 9ceebbe7-9607-4552-8764-876e47032660
```

You store the header value as a *secret* in AWS Secrets Manager\. When your CDN sends a playback request, MediaPackage verifies that the secret's value matches the custom HTTP header value\. MediaPackage is given permission to read the secret via an AWS Identity and Access Management permissions policy and role\.

Secret key and example value\.

```
{“MediaPackageCDNIdentifier”: "9ceebbe7-9607-4552-8764-876e47032660"}
```

If the values match, MediaPackage serves the content along with an HTTP `200 OK` status code\. If it's not a match, or if the authorization request fails, then MediaPackage doesn't serve the content, and sends an HTTP `403 Unauthorized` status code\.

The following image shows successful CDN authorization using Amazon CloudFront\.

![\[The image shows a successful CDN authentication flow. The bottom left shows a playback device requesting content from Amazon CloudFront indicated by an arrow. CloudFront includes the custom HTTP header and value in it's request to MediaPackage, indicated by an arrow. MediaPackage requests the secret info from AWS Secrets Manager, indicated by an arrow, which is dependent on permission from IAM. AWS Secrets Manager responds with the secret value to MediaPackage. MediaPackage verifies that the secret matches the header value, which is indicated by a green checkbox. MediaPackage sends an HTTP 200 OK status code along with video content to CloudFront. CloudFront serves the video content to the playback device.\]](http://docs.aws.amazon.com/mediapackage/latest/ug/images/cdn_auth.png)

For step\-by\-step instructions on how to set up CDN authorization, see [Setting up CDN authorization](cdn-auth-setup.md)\.