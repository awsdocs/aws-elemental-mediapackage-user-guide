# Access control fields<a name="endpoints-hls-access-control"></a>

1. To enable this endpoint to serve content to requesting devices, select **Allow origination**\. It is uncommon to disallow origination on an endpoint\. Typically, the only reason that you won't allow an endpoint to serve content is if it's only being used to harvest VOD content from the live stream\. For more information, see [Creating live\-to\-VOD assets with AWS Elemental MediaPackage](ltov.md)\.

1. To serve content to all requesting IP addresses, choose **Allow all incoming clients**\. To limit the IP addresses that this endpoint serves, use these fields: 
**Note**  
Only IPv4 addresses are allowed\.

   1. Select **Restrict by IP address**\.

   1. In **Whitelist**, type the IP addresses that this endpoint serves content to\.

1. To require that content requests to this endpoint include a valid authorization code, select **Use authorization**\. Complete the remaining fields:

   1. In **Secrets role ARN**, enter the ARN for the IAM role that grants MediaPackage access to AWS Secrets Manager\.

   1. In **CDN identifier secret**, enter the ARN for the authorization code secret in Secrets Manager\.

   For information about how this authorization works, see [CDN authorization in AWS Elemental MediaPackage](cdn-auth.md)\.