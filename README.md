# Home Assistant Add-ons

Home Assistant add-ons for RTL-SDR, RTL_433 and MQTT. Receive wireless sensor data and bring it directly into Home Assistant.

## Installation

Add the repository URL under **Settings → Add-ons → Add-on Store → ⋮ → Repositories**:

```text
https://github.com/qpman87/hassio_addons
```

## Available Add-ons

### SDR2MQTT

Receive wireless sensor data using an RTL-SDR-compatible USB receiver and [RTL_433](https://github.com/merbanan/rtl_433), then publish it to Home Assistant via MQTT.

- Automatic Home Assistant MQTT discovery.
- No separate RTL_433 add-on or helper add-ons required.
- Supports RF devices compatible with RTL_433.
