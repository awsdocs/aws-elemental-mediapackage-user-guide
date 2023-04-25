# Stream selection fields<a name="endpoints-smooth-include-streams"></a>

Define the streams to include\.

The minimum and maximum values take into account only the video bitrates\. If the video bitrate is *below the minimum* specified rate, it's *not* included in the output, regardless of the sum of the bitrates for other tracks\. Likewise, if the video bitrate is *below the maximum *specified rate, it *is* included in the output, regardless of the sum of the bitrates for other tracks\.

1. \(Optional\) For **Stream order**, choose the order that video bitrates are presented to the player\.
   + **Original** to sort the output streams in the same order that the incoming source uses\.
   + **Video bitrate ascending** to sort the output streams starting with the lowest bitrate and ending with the highest\.
   + **Video bitrate descending** to sort the output streams starting with the highest bitrate and ending with the lowest\.

1. \(Optional\) For **Min video bitrate**, enter the minimum bitrate \(in bits per second\) that video tracks must be at or above to be available for playback from this endpoint\.

1. \(Optional\) For **Max video bitrate**, enter the maximum bitrate \(in bits per second\) that video tracks must be at or below to be available for playback from this endpoint\.