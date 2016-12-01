# xmas-hat snap

This snap demonstrates face detection through OpenCV and applies a silly Christmas hat layer on detected faces. Results to be seen on port 8080.

![](http://i.imgur.com/5ZbOrYP.png?1)

This snap is a _christmas-ified_ version of https://github.com/ubuntu/face-detection-demo.


## Setup your rpi2/3

1. Install [ubuntu core](https://developer.ubuntu.com/en/snappy/) on your Raspberry Pi.
1. Plug a USB webcam into your Raspberry Pi
1. Install this snap: `snap install xmas-hat --edge --devmode`


## See the results

The webserver in the snap will be launched automatically as a service after install and when your board starts.

You can launch a web browser on the same network and point it to `http://<ip-address-of-the-pi>:8080` to see the output of the face detection results. A capture is taken from the webcam every 5 seconds and the end picture will only be updated when a face is detected.

### Increasing the capture rate

You can install this snap on any device running Ubuntu Core, and on more powerful devices (like an x86 laptop), you may want to increase the frequency of webcam captures.

To do so, simply tweak the value of `nextFrameSec` on [this line](https://github.com/caldav/xmas-hat/blob/master/face-detection-backend/detection/webcam.go#L173), for example changing 5 seconds into 1 second, and rebuild the snap by running `snapcraft` on the project directory.

It will create an `xmas-hat_1.0_<arch>.snap` that you can install by running:

```bash
snap install xmas-hat*.snap --devmode
```

### Disabling the snap

While it can be a fun snap to have installed, you may not want to have your webcam and port 8080 taken by it all the time.

Any snap can be disabled with the `snap disable <snap>` command, stopping any services it runs and effectively making it unavailable to the system:

```
snap disable xmas-hat
```

To enable a disabled snap, use `snap enable <snap>`.
