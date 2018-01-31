# Working with Endpoints in AWS Elemental MediaPackage<a name="endpoints"></a>

An endpoint defines a single delivery point of a channel\. The endpoint holds all the information that is needed for AWS Elemental MediaPackage to integrate with a player or content distribution network \(CDN\) such as Amazon CloudFront\. Configure the endpoint to output content in one of the available stream formats:

Additionally, the endpoint holds information about digital rights management \(DRM\) and encryption integration, stream bit rate presentation order, and more\.

When you create an endpoint, it provides a public URL that is fixed\\ for the lifetime of the endpoint, regardless of any failures or upgrades that might happen over time\. This URL is how the player or CDN accesses the stream from the endpoint\.


+ [Creating an Endpoint](endpoints-create.md)
+ [Viewing All Endpoints Associated with a Channel](endpoints-view-all.md)
+ [Viewing a Single Endpoint](endpoints-view-one.md)
+ [Editing an Endpoint](endpoints-edit.md)
+ [Deleting an Endpoint](endpoints-delete.md)
+ [Previewing an Endpoint](endpoints-preview.md)