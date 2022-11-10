# Access control fields<a name="endpoints-hls-access-control"></a>

Define the access control values\.

1. Select **Allow origination** to enable this endpoint to serve content to requesting devices\. It is uncommon to disallow origination on an endpoint\.

   Typically, the only reason that you won't allow an endpoint to serve content is if it's only being used to harvest VOD content from the live stream\. For more information, see [Creating live\-to\-VOD assets with AWS Elemental MediaPackage](ltov.md)\.

1.  Choose **Allow all incoming clients** to serve content to all requesting IP addresses and ranges or choose **Restrict by IP address** to limit the IP addresses that this endpoint serves\. If you restrict by IP address, for **IP allowlist**, enter the IP addresses and ranges that this endpoint serves content to\. One CIDR block per line\. 
**Note**  
Only IPv4 addresses are allowed\.

1.  Select **Use CDN authorization** to require that content requests to this endpoint include a valid authorization code\. Complete the remaining fields:

   1. For **Secrets role ARN**, enter the ARN for the IAM role that grants MediaPackage access to AWS Secrets Manager\. The Secrets role ARN must be in this format: `arn:aws:iam::accountID:role/name`

   1. For **CDN identifier secret ARN**, enter the ARN for the authorization code secret in Secrets Manager that your CDN uses for authorization to access your endpoint\. The CDN identifier secret ARN must be in this format: arn:aws:secretsmanager:*region*:*accountID*:secret*guid*\.

   For information about how this authorization works, see [CDN authorization in AWS Elemental MediaPackage](cdn-auth.md)\.