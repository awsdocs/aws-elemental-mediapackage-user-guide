# Working with endpoints in AWS Elemental MediaPackage<a name="endpoints"></a>

An endpoint defines a single delivery point of a channel\. The endpoint holds all the information that's needed for AWS Elemental MediaPackage to integrate with a player or content delivery network \(CDN\) such as Amazon CloudFront\. Configure the endpoint to output content in one of the available stream formats:
+ Apple HLS – Packages content to Apple HTTP Live Streaming \(HLS\)
+ Microsoft Smooth – Packages content for Microsoft Smooth Streaming players
+ Common Media Application Format \(CMAF\) – Packages content to devices that support Apple HLS fragmented MP4 \(fMP4\)
+ DASH\-ISO – Packages content for the DASH\-ISO ABR streaming protocol

Additionally, the endpoint holds information about digital rights management \(DRM\) and encryption integration, stream bitrate presentation order, and more\.

**Topics**
+ [Creating an endpoint](endpoints-create.md)
+ [Viewing all endpoints associated with a channel](endpoints-view-all.md)
+ [Viewing a single endpoint](endpoints-view-one.md)
+ [Editing an endpoint](endpoints-edit.md)
+ [Deleting an endpoint](endpoints-delete.md)
+ [Previewing an endpoint](endpoints-preview.md)