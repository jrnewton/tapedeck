# Tapedeck

Archive radio streams to the cloud.

Components:
* [Client](https://github.com/jrnewton/tapedeck-client) implemented in Vue 3.
* [APIs](https://github.com/jrnewton/tapedeck-api) implemented in AWS-SAM/Lambda functions.


## Archive an existing stream archive

Provide a stream archive URL (m3u format).
Download mp3 file(s) and store in the cloud.

### Example

URL - https://wmbr.org/m3u/Backwoods_20201031_1000.m3u
Expands out to

```
#EXTM3U
#EXTINF:7443,Backwoods
http://wmbr.org/archive/Backwoods____10_31_20_9:58_AM.mp3
```

## Schedule recording of a live stream

Define a time window to capture a live stream.
Time window will be exact to content length.
Capture will be +/- 2 minutes on each end.

### Example

URL - http://wmbr.org:8000/hi

## Cloud Storage

Store in S3 to start. Consider moving data to glacier as well.

Would be really nice to also push to my Google drive for easy download/listening via GoPlayer.

## Phases

- POST function will consume M3U URL, store first MP3 file direct in S3 with no additional processing.
- same as previous but queue each MP3 in playlist to another function will process and store into S3.
- same as previous but capture MP3 metadata via another function.
- same and store metadata in DynamoDB
```
  MP3 item psuedo schema
  {
    userid: string,
    resourceName: string,
    url: string,
    metadata: {
      . . .
    },
    playlist: {
      url: string,
      ... other meta data
    }
  }
```

