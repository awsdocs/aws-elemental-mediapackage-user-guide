# Time\-shifted Viewing Reference in AWS Elemental MediaPackage<a name="time-shifted"></a>

*Time\-shifted viewing* means that viewers can start watching a live stream at a time earlier than "now," allowing them to join from the beginning a show that's already in progress or to watch a show that's already completed\. AWS Elemental MediaPackage allows a content retention window of up to 72 hours for time\-shifted viewing\. Time\-shifted functionality is controlled by the MediaPackage endpoint and by the start and end parameters provided in the content request URL\. 

**To enable time\-shifted viewing**

1. Enable time\-shifted viewing by typing a value for **Startover time** on the AWS Elemental MediaPackage endpoint object\. You can do this through either the MediaPackage console or the REST API\. 

   When requests with start and end parameters are sent to this endpoint, AWS Elemental MediaPackage generates a manifest within the window that is indicated in the request\. If no start and end parameters are used, the service generates a standard manifest\.
**Note**  
You might notice that the manifest lags behind real time when you initially create a startover window on an endpoint\. This is because AWS Elemental MediaPackage starts filling the manifest from the start of the window, and works up to "now\." So if you have a 24\-hour startover window, MediaPackage fills the manifest starting 24 hours ago and working up to "now\."

1. Ensure that content requests contain start and end parameters as needed\. AWS Elemental MediaPackage accepts requests for up to six hours of content\. 

   For packager\-specific rules about how you can notate the parameters, see [Rules for Start and End Parameters](#start-and-end-parameters-rules)\.

   The start and end parameters determine the time boundaries of the manifest\. Expected behaviors are as follows:
   + If both start and end parameters are used in the URL, the resulting manifest has a fixed start and end point that correspond to the specified start and end parameters\.
   + If a start parameter is specified but not an end, the resulting manifest has a fixed start point that corresponds to the specified start parameter, and the end of the manifest grows as the live content progresses\. You can use a start time that’s up to 6 hours in the past\.
   + If an end parameter is specified but no start, the resulting manifest starts "now" and has a fixed endpoint that corresponds to the specified end parameter\.
   + If no parameters are specified, a standard manifest is generated starting "now" with no endpoint\.

## Rules for Start and End Parameters<a name="start-and-end-parameters-rules"></a>

Start and end parameters denote the beginning and end of a time\-shifted manifest\. The playback device can append parameters to the end of a manifest request or include the parameters within the request\. 

In all cases, the date and time must be notated in one of the following formats:
+ ISO 8601 dates, such as 2017\-08\-18T21:18:54\+00:00
+ POSIX \(or Epoch\) time, such as 1503091134

The following topics describe the location rules by packager type\.

**Topics**
+ [DASH Parameter Rules](#parameter-rules-dash)
+ [HLS and CMAF Parameter Rules](#allowed-parameter-location-hls)
+ [Microsoft Smooth Parameter Rules](#allowed-parameter-location-mss)

### DASH Parameter Rules<a name="parameter-rules-dash"></a>

Start and end parameters in the URL request for DASH content can use standard parameter notation, or can be included as path elements in the URL\. 
+ Query parameter notation – start and end parameters are included at the end of the request URL  
**Example**  

  ```
  https://cf98fa7b2ee4450e.mediapackage.us-east-1.amazonaws.com/out/v1/997cbb27697d4863bb65488133bff26f/sports.mpd?start=1513717228&end=1513720828
  ```
+ Path elements – start and end parameters are included in the path of the request URL  
**Example**  

  ```
  https://cf98fa7b2ee4450e.mediapackage.us-east-1.amazonaws.com/out/v1/997cbb27697d4863bb65488133bff26f/start/2017-12-19T13:00:28-08:00/end/2017-12-19T14:00:28-08:00/sports.mpd
  ```

### HLS and CMAF Parameter Rules<a name="allowed-parameter-location-hls"></a>

Start and end parameters in the URL request for HLS content can use standard parameter notation, or can be included as path elements in the URL\. The rules for HLS and CMAF are the same, except that when you're inserting path elements in the CMAF endpoint, the elements have to be after the manifest ID in the URL\.
+ Query parameter notation – start and end parameters are included at the end of the request URL  
**Example HLS**  

  ```
  https://cf98fa7b2ee4450e.mediapackage.us-east-1.amazonaws.com/out/v1/064134724fd74667ba294657a674ae72/comedy.m3u8?start=2017-12-19T13:00:28-08:00&end=2017-12-19T14:00:28-08:00
  ```  
**Example CMAF**  

  ```
  https://cf98fa7b2ee4450e.mediapackage.us-east-1.amazonaws.com/out/v1/064134724fd74667ba294657a674ae72/manifest_id/news.m3u8?start=2018-04-04T01:14:00-08:00&2018-04-04T02:15:00-08:00
  ```
+ Path elements – start and end parameters are included in the path of the request URL  
**Example HLS**  

  ```
  https://cf98fa7b2ee4450e.mediapackage.us-east-1.amazonaws.com/out/v1/064134724fd74667ba294657a674ae72/start/1513717228/end/1513720828/comedy.m3u8
  ```  
**Example CMAF**  

  ```
  https://cf98fa7b2ee4450e.mediapackage.us-east-1.amazonaws.com/out/v1/064134724fd74667ba294657a674ae72/manifest_id/start/1522807213/end/1522800013/news.m3u8
  ```

### Microsoft Smooth Parameter Rules<a name="allowed-parameter-location-mss"></a>

Start and end parameters in the URL request for Microsoft Smooth Streaming content can be included as path elements in the URL\. 
+ Path elements – start and end parameters are included in the path of the request URL  
**Example**  

  ```
  https://cf98fa7b2ee4450e.mediapackage.us-east-1.amazonaws.com/out/v1/1f76b3b4f94c44a485c0e4e560afe50e/start/1513717228/end/1513720828/drama.ism/Manifest
  ```