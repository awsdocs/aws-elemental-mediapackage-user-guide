# Document history for User Guide<a name="doc-history"></a>

The following table describes important changes in each release of the *AWS Elemental MediaPackage User Guide* after May 2018\. For notification about updates to this documentation, you can subscribe to an RSS feed\.
+ **API version:** latest

| Change | Description | Date | 
| --- |--- |--- |
| [New CMAF encryption option](endpoints-cmaf-encryption.md) | MediaPackage now supports AES\-CTR encryption to encrypted CMAF endpoints\. | September 2, 2022 | 
| [Updated information regarding SPEKE Version 2\.0 presets](encryption-choosing-speke-version.md) | Updated the CPIX Version to 2\.3\. Updated the SPEKE Version 2\.0 table that describes the support matrix for protocol and DRM system\. | July 19, 2022 | 
| [New documentation of SPEKE Version 2\.0 presets](drm-content-speke-v2-presets.md) | MediaPackage supports SPEKE Version 2\.0 presets for unencrypted tracks and encrypted tracks, a single encryption key for all audio and video tracks, and multiple encryption keys for audio and video tracks\. | July 19, 2022 | 
| [New **Include IFrame only stream** option](endpoints-dash-packager.md) | MediaPackage now supports the **Include IFrame only stream** to include an additional I\-frame only stream\. along with the other tracks in the manifest\. | July 19, 2022 | 
| [Manifest update time](monitoring-manifest-last-updated.md) | MediaPackage playback responses now include custom headers that specify when MediaPackage last updated the manifest\. | January 3, 2022 | 
| [Add information about image\-based trick\-play for HLS live](trick-play.md) | MediaPackage now supports image\-based trick\-play for HLS live\. | November 24, 2021 | 
| [Added support for `includeAudio` parameter](supported-inputs-vod-smil.md) | MediaPackage now supports `includeAudio` in \.smil manifests | November 1, 2021 | 
| [New DVB subtitle option](endpoints-hls-packager.md) | MediaPackage can now passthrough DVB subtitles into packaging configuration outputs\. | October 20, 2021 | 
| [New DVB subtitle option](cfigs-hls-manset.md) | MediaPackage can now passthrough DVB subtitles into the HLS outputs\. | October 20, 2021 | 
| [New trick\-play topic](trick-play.md) | MediaPackage now supports trick\-play for DASH\. | October 15, 2021 | 
| [Asset playback status](pkg-cfig-view.md) | You can now view playable status information about an asset\. This lets you tell whether or not an asset is ready for playback, or if processing has failed\. | October 7, 2021 | 
| [MediaPackage now supports SPEKE Version 2\.0](using-encryption.md) | Added information about SPEKE Version 2\.0\. | September 7, 2021 | 
| [New guidance for integrating with SPEKE Version 2\.0](encryption-choosing-speke-version.md) | MediaPackage now supports SPEKE Version 2\.0\. | September 6, 2021 | 
| [New metadata passthrough topic](metadata-passthrough.md) | MediaPackage now supports ID3 and KLV metadata passthrough\. When ID3 or KLV metadata is present in a channel's input stream, MediaPackage automatically passes through the metadata to the output stream\. | June 30, 2021 | 
| [New CMAF encryption options](cfigs-cmaf-encryption.md) | MediaPackage now offers constant IV and multiple system IDs for CMAF packaging configurations\. | June 30, 2021 | 
| [Updated cost allocation tagging content](tagging.md) | Clarified availability of cost allocation tagging\. | May 27, 2021 | 
| [Added DASH endpoints for live\-to\-VOD](ltov-reqmts.md) | MediaPackage now supports DASH endpoint requirements for live\-to\-VOD\. | May 14, 2021 | 
| [New DASH and CMAF manifest setting](cfigs-dash-manset.md) | Added the **Include encoder configuration in segments** manifest settings option\. If you turn on this option, MediaPackage places Sequence Parameter Set \(SPS\), Picture Parameter Set \(PPS\), and Video Parameter Set \(VPS\) metadata in each video segment instead of in the init fragment\. | April 28, 2021 | 
| [Added `audio_bitrate` query parameter](manifest-filtering.md) | `audio_bitrate` can now be used as a manifest filter query parameter\. | March 22, 2021 | 
| [Access logging](access-logging.md) | MediaPackage now supports access logging for VOD\. | February 24, 2021 | 
| [Added information about MediaPackage event handling behavior for CloudWatch events](cloudwatch-events-example.md) | MediaPackage emits events to CloudWatch on a best effort basis\. | January 7, 2021 | 
| [Access logging](access-logging.md) | MediaPackage now supports access logging, which provides detailed records for the requests that are made to a channel\. This feature is available for live workflows\. | October 21, 2020 | 
| [New UTC Timing option for DASH endpoints](endpoints-dash-packager.md) | MediaPackage now supports UTC timing for DASH endpoints\. | October 20, 2020 | 
| [Support for SCTE\-35 EXT\-x\-DATERANGE tag](scte.md#ext-x-daterange-ad-marker) | Added a new EXT\-X\-DATERANGE section to the SCTE\-35 Ad Marker topic\. | August 7, 2020 | 
| [Moved the maximum live manifest length from hard quota to soft quota](live-quotas.md#live-hard-quotas) | The maximum live manifest length is a soft quota\. Moved this entry from hard quotas to soft quotas\. | June 24, 2020 | 
| [Added information about CDN authorization for VOD](cdn-auth.md) | Added *CDN Authorization in AWS Elemental MediaPackage* topic to describe how to add authorization to requests from your CDN\. | May 29, 2020 | 
| [Updated manifest filtering topic](manifest-filtering.md) | Added 6 new parameters and updated the character limit to 1024\. | May 15, 2020 | 
| [Remove VOD tagging restriction](tagging.md) | MediaPackage now supports tagging for VOD\. | April 23, 2020 | 
| [New manifest filtering topic](manifest-filtering.md) | Added a new *Manifest Filtering* topic\. | April 8, 2020 | 
| [Updated maximum time\-shifted and live\-to\-VOD manifest length](live-quotas.md#live-hard-quotas) | The maximum manifest length is now 24 hours for all supported output formats\. | March 9, 2020 | 
| [New VOD DASH\-ISO manifest console settings](cfigs-dash-manset.md) | Added new DASH\-ISO manifest console settings for VOD packaging configurations\. Compact DASH, new segment template formats, and period trigger options are now available\. | February 25, 2020 | 
| [Multi\-period DASH is now available for both live and VOD\.](multi-period.md) | Removed references to "live only" support for multi\-period DASH\. | February 25, 2020 | 
| [Compact DASH manifests are now available for both VOD and live](compacted.md) | Removed reference to "live only" support for compact DASH\. | February 25, 2020 | 
| [Fixed bug](cloudwatch-events-example.md#hj-status-events) | Successful harvest jobs CloudWatch events return `"status": "SUCCEEDED"`\. | February 10, 2020 | 
| [Added information CDN authorization](cdn-auth.md) | Added *CDN Authorization in AWS Elemental MediaPackage* topic to describe how to add authorization to requests from your CDN\. | December 23, 2019 | 
| [Added information about VOD playback events\.](cloudwatch-events-example.md#input-state-events) | Added example playback ready notification events for ingested VOD content\. | November 8, 2019 | 
| [Added information about live\-to\-VOD CloudWatch Events\.](cloudwatch-events-example.md#hj-status-events) | Added example harvest job notification events for live\-to\-VOD content harvesting\. | October 15, 2019 | 
| [Added \.smil manifest information](supported-inputs-vod-smil.md) | Added *Requirements for \.smil manifests* topic to describe the supported `.smil` manifest format for VOD ingest\. | October 10, 2019 | 
| [Added live\-to\-VOD \(video on demand\) topics\.](what-is.md) | Throughout guide, added and updated topics about creating live\-to\-VOD assets, including *Creating Live\-to\-VOD Assets* and *Live\-to\-VOD Content Delivery*\. | October 1, 2019 | 
| [Updated time\-shifted manifest length limit\.](live-quotas.md#live-hard-quotas) | AWS Elemental MediaPackage can now produce time\-shifted manifests up to 18 hours for DASH with compact manifest, HLS, and CMAF\. | August 21, 2019 | 
| [Added supported inputs and outputs info](supported-inputs.md) | Added *Supported Inputs and Outputs* topic that describes what input types, containers, and codecs MediaPackage supports\. | June 21, 2019 | 
| [Added configurable SCTE\-35 options\.](scte.md) | Added *SCTE\-35 Message Options in AWS Elemental MediaPackage* topic that describes how you can configure MediaPackage behavior when there are SCTE\-35 markers in your input content\. | June 21, 2019 | 
| [Added security chapter\.](security.md) | Added the *Security* chapter to enhance and standardize security topics for MediaPackage\. | June 5, 2019 | 
| [Added video on demand \(VOD\) topics\.](what-is.md) | Throughout guide, added topics about working with VOD content: *VOD Content Processing*, *Allowing MediaPackage to Access Amazon Simple Storage Service*, *VOD Content Delivery*, *Delivering VOD Content*, *VOD Content Metrics*, and *VOD Content Limits*\. | May 17, 2019 | 
| [Added further information about DASH manifest SegmentTemplate format options\.](segtemp-format.md) | Added the *Duration Attribute* topic to discuss how to include duration information in `SegmentTemplate` instead of using `SegmentTimeline`\. | May 10, 2019 | 
| [Updated time\-shifted manifest length limit](live-quotas.md#live-hard-quotas) | AWS Elemental MediaPackage can now produce time\-shifted manifests up to 9 hours\. | May 1, 2019 | 
| [Added information about live and VOD manifests\.](what-is-manifest.md) | Added the *Live and VOD Manifest Reference* topic that explains when MediaPackage serves a live or VOD manifest\. | April 16, 2019 | 
| [Added tagging information](tagging.md) | Added *Tagging Resources* topic to discuss how tagging channels and endpoints works in AWS Elemental MediaPackage\. | March 4, 2019 | 
| [Added information about DASH manifest SegmentTemplate format options\.](segtemp-format.md) | Added the *DASH Manifest Segment Template Format* topic to discuss how to change variables in the media URL in the SegmentTemplate object of the DASH manifest\. | February 6, 2019 | 
| [Added DASH manifest treatment information](dash-trtmts.md) | Added *DASH Manifest Options* topic to discuss the ways that you can modify output DASH manifests\. | February 6, 2019 | 
| [Added AWS CloudTrail logging information\.](logging-using-cloudtrail.md) | Added *Logging AWS Elemental MediaPackage API Calls with AWS CloudTrail* topic to discuss using CloudTrail to log actions in the AWS Elemental MediaPackage API\. | December 21, 2018 | 
| [Added information about compact DASH manifests](compacted.md) | Added a *Compacted DASH Manifests* topic to discuss how compacting DASH output manifests works in AWS Elemental MediaPackage\. | December 18, 2018 | 
| [Updated content retention window limit](live-quotas.md#live-hard-quotas) | AWS Elemental MediaPackage now retains content for 336 hours \(14 days\)\. | November 13, 2018 | 
| [Added content key encryption to DRM encryption](drm-content-key-encryption.md) | Added the option to encrypt content keys\. Prior to this, AWS Elemental MediaPackage supported clear key delivery only\. To use content key encryption, your DRM key provider must support encrypted content keys\. If you enable this feature for a key provider that doesn't handle content key encryption, the operation fails\. | November 8, 2018 | 
| [Added input redundancy information\.](what-is-flow-ir.md) | Added *How Input Redundancy Works* topic to discuss how MediaPackage can receive two identical streams for back\-up purposes\.  | August 28, 2018 | 
| [Added Amazon CloudFront console integration information](cdns.md) | Added sections about working with distributions in CloudFront, including how to create a distribution from the AWS Elemental MediaPackage console\. | August 3, 2018 | 
| [Added information about multi\-period DASH\.](multi-period.md) | Added *Multi\-period DASH in AWS Elemental MediaPackage* topic to discuss the purpose and functionality of multiple periods in DASH manifests\. | July 18, 2018 | 
| [Added CDN information](cdns.md) | Added *Working with CDNs* topic to discuss how AWS Elemental MediaPackage works with CDNs such as Amazon CloudFront\. | May 31, 2018 | 
| [Added information about creating event notifications](monitoring-cloudwatch-events.md) | Added the *Creating Event Notifications* topic that describes how to use Amazon CloudWatch Events and Amazon Simple Notification Service to notify you of new events\. | January 22, 2018 | 

## Earlier updates<a name="earlier-updates"></a>

The following table describes important changes in each release of the *AWS Elemental MediaPackage User Guide* before May 2018\.


****  

| Change | Description | Date | 
| --- | --- | --- | 
| Initial document creation | New document\. | November 27, 2017 | 
| Corrected links and added whitelisting | Corrected links to the AWS Elemental MediaPackage console and AWS Elemental MediaPackage API Reference\.In Working with Endpoints, added reference to access control fields\. | December 1, 2017 | 
| Added IAM policy information specific to AWS Elemental MediaPackage | In [Setting up AWS Elemental MediaPackage](setting-up.md), added instructions for creating non\-admin roles with limited permissions\. | December 13, 2017 | 
| Added hard limit information | In [Quotas in AWS Elemental MediaPackage](quotas.md), added information about limits that can't be changed \(hard limits\)\. | December 20, 2017 | 
| Updated IAM policy information | In [Setting up AWS Elemental MediaPackage](setting-up.md), added information about policies specific to AWS Elemental MediaPackage\. | January 5, 2018 | 
| Added CMAF endpoint information | Added [Creating a CMAF endpoint](endpoints-cmaf.md) section for new output type\. | April 6, 2018 | 
| Updated feature functionality | In [Features of AWS Elemental MediaPackage](what-is-features.md), added feature support for HDR\-10\. | April 30, 2018 | 
| Added CDN information | Added topic [Working with Content Delivery Networks \(CDNs\)](cdns.md) to discuss how AWS Elemental MediaPackage works with CDNs such as Amazon CloudFront\. | May 31, 2018 | 

**Note**  
The AWS Media Services are not designed or intended for use with applications or in situations requiring fail‐safe performance, such as life safety operations, navigation or communication systems, air traffic control, or life support machines in which the unavailability, interruption or failure of the services could lead to death, personal injury, property damage or environmental damage\.