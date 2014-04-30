RoverApp
========

Time-delay video feed for a remote-controlled rover.


## About

This web application uses images from a webcam to generate a time-delayed video feed for simulating transmission delay to-and-from a rover on the Moon, etc.

## Demo

* See http://kiwispace.github.io/RoverApp/

## Requirements

* Wifi camera that allows you to read the current view as an image  (e.g. http://192.168.1.1/image.jpg)
* and, if running the application from a website, the camera must support CORS-requests, otherwise you'll get a javascript access error (**see below**)

## How it works

The application downloads the image from the webcam every 200ms (or as customised), creating a 5-frame-per-second live video feed. The default delay is about 0.2 milliseconds, or basically real-time. 

As you increase move the delay slider, storage buckets are created - and the fetched image stored there until ready to be displayed. You can change the slider at any time, but it will take several seconds (whatever the delay is set to) to re-buffer the video feed.

## Setup
On first-load, you will see a 'buffering' image in the picture display. Go to the 'Camera Setup' button, and enter the IMAGE-URL as required for your camera. Hit save, and then the video feed should appear. The data is written to a cookie, and will be persisted between loads.

## Cross-Domain Access
When using the application on a website (e.g. the demo site), the webcam you're accessing needs to allow access to the remote site. Otherwise you'll seen an error in the javascript console like:

> [Error] XMLHttpRequest cannot load http://your.webcam/image.jpg?r=1398894278824. Origin http://kiwispace.github.io is not allowed by Access-Control-Allow-Origin. (RoverApp, line 0)

In general, most webcams don't appear to support this header.

We found in our testing, that if you download the files and run them from your **local disk** (e.g. file:// url) that this issue didn't pop up.

**WORKAROUND:** You can also instruct your web browser to disable file security, and allow access.

e.g. for Google Chrome on Mac:
> /Applications/Google\ Chrome.app/Contents/MacOS/Google\ Chrome **--disable-web-security**


License
----

* MIT
* Attribution appreciated - "KiwiSpace Foundation"

**Free Software, Hell Yeah!**

