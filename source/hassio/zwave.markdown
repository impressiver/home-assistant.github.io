---
layout: page
title: "Z-Wave"
description: "Instructions on how-to use Z-Wave with Hass.io."
date: 2017-04-30 13:28
sidebar: true
comments: false
sharing: true
footer: true
---

To enable Z-Wave, plug your Z-Wave USB stick into your Raspberry Pi 3 and add the following to your `configuration.yaml`:

```yaml
zwave:
  usb_path: /dev/ttyACM0
```

If you need GPIO on Raspberry Pi 3 for your Z-Wave module, add the following line into `config.txt`:

```
dtoverlay=pi3-miniuart-bt
```

For some devices the `/dev/ttyAMA0` device is not detected by udev and is therefore not mapped by Docker. To explicitly set this device for mapping to Home-Assistant, execute the following command using the ssh add-on:

```bash
$ curl -d '{"devices": ["ttyAMA0"]}' http://hassio/homeassistant/options
```

After that, you need to change `usb_path` to `/dev/ttyAMA0`.

### HUSBZB-1:

```yaml
zwave:
  usb_path: /dev/ttyUSB0
  
zha:
  usb_path: /dev/ttyUSB1
  database_path: /config/zigbee.db
```
