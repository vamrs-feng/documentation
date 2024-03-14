---
sidebar_position: 4
---

# Raspberry Camera v2

## Configuration

- Prepare the raspberry camera v2 and connect it to the NX5 IO via the FPC cable.

- Open console and run `sudo rsetup` command.

```bash
radxa@radxa-nx5-io:~$ sudo rsetup
```

- Pass the [device tree configuration](../radxa-os/sys-config/rsetup#overlays) to enable overlay for the raspberry camera v2.

:::caution [Caution]

1. Please enable the `[] Enable Raspberry Pi Camera v2 on CAM0` item overlay.
2. Quit and reboot after enabling successfully displaying `[*] Enable Raspberry Pi Camera v2 on CAM0` for the configuration to take effect.

:::

## Testing

You can also open the camera preview using the terminal command.

```bash
gst-launch-1.0 v4l2src device=/dev/video11 io-mode=4 ! videoconvert ! video/x-raw,format=NV12,width=1920,height=1080 ! xvimagesink;
```

Take a picture with the following command.

```bash
gst-launch-1.0 v4l2src device=/dev/video11 io-mode=4 ! videoconvert ! video/x-raw,format=NV12,width=1920,height=1080 ! jpegenc ! multifilesink location=file.name.jpg;
```

Take a video with the following command:

```bash
gst-launch-1.0 v4l2src num-buffers=512 device=/dev/video11 io-mode=4 ! videoconvert ! video/x-raw, format=NV12, width=1920, height=1080, framerate=30/1 ! tee name=t ! queue ! mpph264enc ! queue ! h264parse ! mpegtsmux ! filesink location=/home/radxa/file.name.mp4
```
