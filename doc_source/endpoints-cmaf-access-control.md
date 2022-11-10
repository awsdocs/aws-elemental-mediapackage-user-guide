# Access control fields<a name="endpoints-cmaf-access-control"></a>

Define the access control values\.

1. To enable this endpoint to serve content to requesting devices, select **Allow origination**\. It's uncommon to disallow origination on an endpoint\.

   Typically, the only reason that you won't allow an endpoint to serve content is if it's only being used to harvest VOD content from the live stream\. For more information, see [Creating live\-to\-VOD assets with AWS Elemental MediaPackage](ltov.md)\.

1. To serve content to all requesting IP address, choose **Allow all incoming clients**\. To limit the IP addresses that this endpoint serves, use these fields:

   1. Select **Restrict by IP address**\.

   1. In **IP allowlist**, enter the IP addresses and ranges that this endpoint serves content to\. One CIDR block per line\.

1. To require that content requests to this endpoint include a valid authorization code, select **Use CDN authorization**\. Complete the remaining fields:

   1. In **Secrets role ARN**, enter the ARN for the IAM role that grants MediaPackage access to AWS Secrets Manager\.

   1. In **CDN identifier secret ARN**, enter the ARN for the authorization code secret in Secrets Manager\.

   For information about how this authorization works, see [CDN authorization in AWS Elemental MediaPackage](cdn-auth.md)\.