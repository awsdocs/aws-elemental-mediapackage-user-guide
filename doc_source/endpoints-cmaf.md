# Creating a Common Media Application Format \(CMAF\) Endpoint<a name="endpoints-cmaf"></a>

Create an endpoint that formats HEVC content for devices that support Apple HLS fragmented MP4 \(fMP4\)\.

**To create a CMAF endpoint \(console\)**

1. Access the channel that the endpoint will be associated with, as described in [Viewing Channel Details](channels-view.md)\.

1. On the details page for the channel, choose either **Add and edit endpoint** or **Add endpoints** if there are no existing endpoints\.

1. Complete the fields as described in the following topics:
   + [New Endpoint Fields](endpoints-cmaf-new.md)
   + [Packager Settings Fields](endpoints-cmaf-packager.md)
   + [HLS Manifest Fields](endpoints-cmaf-manifest.md)
   + [Encryption Fields](endpoints-cmaf-encryption.md)
   + [Access Control Fields ](endpoints-cmaf-access-control.md)
   + [Streams to Include Fields](endpoints-cmaf-include-streams.md)

1. Choose **Save endpoints**\.

   The new endpoint is displayed in the endpoints section of the channel's details page\.

   The endpoint is active and can deliver content as soon as requests are sent to its URL endpoints\. AWS Elemental MediaPackage scales resources up and down to allow the right amount of capacity for your traffic\.