# Deleting an endpoint<a name="endpoints-delete"></a>

Endpoints can serve content until they're deleted\. Delete the endpoint if it should no longer respond to playback requests\. You must delete all endpoints from a channel before you can delete the channel\.

**Warning**  
If you delete an endpoint, the playback URL stops working\.

You can use the AWS Elemental MediaPackage console, the AWS CLI, or the MediaPackage API to delete an endpoint\. For information about deleting an endpoint through the AWS CLI or MediaPackage API, see the [AWS Elemental MediaPackage API Reference](https://docs.aws.amazon.com/mediapackage/latest/apireference/)\.

**To delete an endpoint \(console\)**

1. Access the channel that the endpoint is associated with, as described in [Viewing channel details](channels-view.md)\.

1. On the details page for the channel, under **Origin endpoints**, select the origin endpoint that you want to delete\.

1. Select **Delete**\.

1. In the **Delete endpoints** confirmation dialog box, choose **Delete**\.