# Working with channels in AWS Elemental MediaPackage<a name="channels"></a>

A channel holds all the information that AWS Elemental MediaPackage \(MediaPackage\) requires to receive a live content stream from a source such as AWS Elemental MediaLive or another encoder\. The channel receives content, and after packaging it, outputs it through an endpoint to downstream devices \(such as video players or CDNs\) that request the content\. 

After you create a channel, MediaPackage provides a pair of input URLs that are fixed for the lifetime of the channel, regardless of any failures or upgrades that might happen over time\. The output of the upstream encoder points to the URLs for stream delivery to MediaPackage\.

For supported live inputs and codecs, see [Live supported codecs and input types](supported-inputs-live.md)\.

**Topics**
+ [Creating a channel](channels-create.md)
+ [Viewing channel details](channels-view.md)
+ [Editing a channel](channels-edit.md)
+ [Rotating credentials on an input URL](channels-rotate-creds.md)
+ [Deleting a channel](channels-delete.md)
+ [Adding an endpoint to a channel](channels-add-endpoint.md)