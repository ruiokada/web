# MPEG DASH Demo

A simple implementation of MPEG-DASH video streaming using the [video.js](http://videojs.com) HTML5 video player and [dash.js](https://github.com/Dash-Industry-Forum/dash.js/) MPEG-DASH client.

## About MPEG-DASH

When streaming videos through the `video` HTML element, the browser must first download the video file entirely before playback can start. This is a problem when the video file is very large and so MPEG-DASH can be used to work around this.

The idea is that the video file is split (or _fragmented_) into shorter videos and a special video player downloads and plays each file subsequently.

## Video File Prep

In order to serve the file using MPEG Dash, the file must be appropriately encoded with H.264 video and AAC audio (i.e. an mp4 video file) before being fragmented. This can be done with `ffmpeg` and `mp4box` using the following commands:

Encoding: `ffmpeg -i [INPUTFILE] -c:v libx264 -b:v 1450k -bf 2 -g 90 -sc_threshold 0 -c:a aac -strict experimental -b:a 96k -ar 32000 [OUTPUTFILE]`

Fragmenting: `mp4box -dash 5000 -profile "dashavc264:live" [INPUTFILE]#audio [INPUTFILE]#video -out "[OUTPUTFILE]"`

[demo-page]: https://web.rso.io/mpeg-dash-demo "MPEG-DASH Demo"
