# Streams to include fields<a name="endpoints-hls-include-streams"></a>

Define the streams to include\.

1. \(Optional\) For **Stream order**, choose from the following:
   + **Original** to sort the output streams in the same order that the incoming source uses\.
   + **Video bitrate ascending** to sort the output streams starting with the lowest bitrate and ending with the highest\.
   + **Video bitrate descending** to sort the output streams starting with the highest bitrate and ending with the lowest\.

1. To make all incoming streams available for playback from this endpoint, select **Include all incoming streams**\.

1. To limit which incoming streams are available for playback from this endpoint, select **Filter incoming streams** and enter filter criteria:
   + \(Optional\) For **Min video bitrate**, enter the minimum bitrate \(in bits per second\) that video tracks must meet to be available for playback from this endpoint\.
   + \(Optional\) For **Max video bitrate**, enter the maximum bitrate \(in bits per second\) that video tracks can have to be available for playback from this endpoint\.

     The minimum and maximum values take into account only the video bitrates\. If the video bitrate is *below the minimum* specified rate, it is *not* included in the output, regardless of the sum of the bitrates for other tracks\. Likewise, if the video bitrate is *below the maximum *specified rate, it *is* included in the output, regardless of the sum of the bitrates for other tracks\.