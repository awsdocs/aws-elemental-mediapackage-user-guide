# Live\-to\-VOD requirements<a name="ltov-reqmts"></a>

Keep in mind these requirements when you're creating live\-to\-VOD assets in AWS Elemental MediaPackage\.

**Endpoint requirements**  
The endpoint that you're harvesting the live\-to\-VOD asset from must meet these requirements:
+ Startover must be enabled and have a **startover window** of 14 days or less\. To check or change the size of the window, see [Viewing a single endpoint](endpoints-view-one.md)\.
+ Your endpoint must serve either clear \(unencrypted\) or encrypted DASH or HLS content\.
+ For DASH endpoints \- Your DASH endpoint must use either the **Number with timeline** or **Time with timeline** segment template format\. For information about creating DASH endpoints, see [Creating a DASH endpoint](endpoints-dash.md)\. 
+ MediaPackage VOD doesn't currently support the ingestion of encrypted assets\. If you're using your harvested assets in an MediaPackage video on demand workflow and your endpoint is encrypted, create an unencrypted shadow endpoint on the same channel\. To do this, deselect **allow origination** so that the new endpoint can't be used for playback\. MediaPackage creates the URL for endpoints that don't have origination enabled, but MediaPackage responds with an error to playback requests sent to this endpoint\.

**Live\-to\-VOD asset requirements**  
The live\-to\-VOD asset must meet these requirements:
+ Its start time must fall on or after the encoder's start time\.
+ Its start and end times must be within the startover window on the endpoint\.
+ Its duration must not exceed the maximum live\-to\-VOD manifest length, which is 24 hours\.