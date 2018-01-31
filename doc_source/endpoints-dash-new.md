# New Endpoint Fields<a name="endpoints-dash-new"></a>

1. For **ID**, type a name that describes the endpoint\. The ID is the primary identifier for the endpoint, and must be unique for your account in the region\.

1. \(Optional\) For **Description**, type any descriptive text that helps you to identify the endpoint later\. 

1. For **Manifest name**, type a short string that will be appended to the end of the endpoint URL\. The manifest name helps to create a unique path to this endpoint\.

1. \(Optional\) To allow time\-shifted playback \(start\-over and catch\-up TV\), select **Startover window** and type the maximum amount of time that viewers can seek back on content\. For more information about implementing start\-over and catch\-up TV, see [[ERROR] BAD/MISSING LINK TEXT](time-shifted.md)\.

1. \(Optional\) To delay when content is available to players, type the duration \(in seconds\) for the delay in **Time delay**\. The minimum time is five seconds\. The maximum time is 86,400 seconds \(24 hours\)\.

   Use time delay to redefine the live point and make content available at a time that equals "now" minus the delay specified\. With a 60\-second time delay, content that AWS Elemental MediaPackage receives at 12:20 isn't available until 12:21\. Requests for playback at 12:20 will be served with content from 12:19\. Likewise, if you're serving content across time zones, you can set a time delay equal to the time zone difference to make content available at, for example, 8:00 local time\.

   When you use time delay in conjunction with a startover window, the time delay duration must be less than the startover window duration\.