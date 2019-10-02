# Destination<a name="hj-create-destination"></a>

The destination information defines how MediaPackage saves the live\-to\-VOD asset after it has been harvested from the live stream\.

1. For **IAM role**, enter the Amazon Resource Name \(ARN\) for the IAM role that provides MediaPackage access to read and write from your Amazon S3 bucket where the live\-to\-VOD asset will be stored\.

1. For **S3 bucket name**, enter the bucket where you want MediaPackage to store the live\-to\-VOD asset\.

1. For **Manifest key**, enter the path within the bucket to the live\-to\-VOD asset, including the file name for the parent manifest of the asset\. If the directory structure doesn't already exist in the bucket, MediaPackage creates it\. 