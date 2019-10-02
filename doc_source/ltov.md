# Creating Live\-to\-VOD Assets with AWS Elemental MediaPackage<a name="ltov"></a>

A live\-to\-VOD \(video on demand\) asset is a portion of a live stream that's been extracted and saved for playback later\. For example, you might save clips from a game for a highlight reel, or a clip of a broadcast show to use later in advertisements for the show\.

To create a live\-to\-VOD asset in MediaPackage, create a harvest job resource\. The harvest job is a request that you create for MediaPackage to extract a portion of a live stream and save the clip as a live\-to\-VOD asset in an Amazon S3 bucket\. The job runs once, then MediaPackage keeps a record of it on your account for 90 days\. This record is for reference purposes only\. You can't delete or modify it\.

The following topics provide more information about live\-to\-VOD assets in MediaPackage\.

**Topics**
+ [Live\-to\-VOD Requirements](ltov-reqmts.md)
+ [How Live\-to\-VOD Works](ltov-how.md)
+ [Working with Harvest Jobs](harvest-jobs.md)