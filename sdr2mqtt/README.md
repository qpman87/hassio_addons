# Home Assistant Add-on: SDR2MQTT
> **Simple installation – just install and play!**
>
> No separate RTL_433 add-on or additional helper add-ons are required. Everything needed to receive and forward your sensor data is included.
>
> **Tested with:** DVB-T2 USB TV stick (RTL-SDR compatible).
>
> Simply install the add-on, enter your MQTT credentials, select the frequency and protocol IDs used by your sensors, and start it. That is it!


A Home Assistant addon for a software defined radio tuned to listen for RF transmissions from SDR/RTL Sensors and republish the data via MQTT.

## About this fork

This add-on is an updated and maintained fork of the original SDR2MQTT add-on by Jeffrey Stone (Slacker Labs).

I created this fork because the original project was no longer actively maintained. As a result, compatibility issues arose with newer Home Assistant releases, and the original add-on could no longer be installed on newer Home Assistant versions starting around May 2026.

Rather than let this useful project become unusable, I decided to continue its development, update its build system, fix compatibility issues, and keep it working with modern Home Assistant installations.

**What you should know:**
- This project is based on the original work by Jeffrey Stone.
- Original copyright notices and attribution are preserved.
- The fork is independently maintained by Edgar Vasilenco.
- It includes compatibility fixes, updated builds and ongoing improvements.

Thanks to Jeffrey Stone for creating the original project and making this continuation possible.


## Installation

Add the repository URL under **Supervisor → Add-on store → ⋮ → Manage add-on repositories**:

    https://github.com/qpman87/hassio_addons

Then search for `SDR to home Assistant` and install it.

## Configuration

Example add-on configuration:

```yaml
mqtt_host: 192.168.x.x
mqtt_user: mqtt_user
mqtt_password: mqtt_pass
mqtt_topic: rtl_433
mqtt_retain: 'true'
frequency: '-f 433.92M'
protocol: '-R 12 -R 91'
units: 'si'
discovery_prefix: homeassistant
discovery_interval: 600
debug: false
```

### Option: `mqtt_host`

The `mqtt_host` option is the ip address of your mqtt server. If you are using the embeded server in Home Assistant just use your instances ip address.

### Option: `mqtt_user`

This is the username required to access your mqtt server.

### Option: `mqtt_password`

The password of the mqtt user account.

### Option: `mqtt_topic`

This si the topic your devices will use.

### Option: `mqtt_retain`

Setting this to `true` means the mqtt server will keep your last value 
until it is changed. Setting it to `false` means the server will forget values after a period of time, 
so you will onyl see a valus it one has been sent recently.

### Option: `frequency`

This sets the frequecy your SDR will listen for. Default is '-f 433.92M' but you could use '-f 915M' or '-f 868M'
of you could use mutliples like '-f 433.92M f 915M'  

### Option: `protocol`

This determines which RTL_433 decoders the software listens to. By default, SDR2MQTT listens for Oregon Scientific sensors (`-R 12`) and InFactory / nor-tec / FreeTec sensors (`-R 91`). You can add or change decoder IDs to support other devices. See the [RTL_433 supported devices](https://github.com/merbanan/rtl_433) for the available protocols.

### Option: `expire_after`

This is a `integer` value that will set an individual sensor entity to `unknown` if no payload is received within the specified seconds. The default value of 0 disables this feature.

### Option: `units`

Sets the meansurement units. 
- `si` = Metric
- `customary` = Imperial / Customary  

### Option: `discovery_prefix`

The mqtt prefix for autodiscovery. `homeassistant` should work. If you use another autodiscovery may not work.

### Option: `discovery_interval`

`600` means Home Assisatnt will check for new devices every 600 seconds. 

### Option: 'debug'

Set debug to `true` if you want to see extra logging. This is noisy though, so I would only run it when actively troubleshooting. Leave at false all other times. 

## Known issues and limitations

- This add-on is totally beta. 

## Changelog & Releases

This repository keeps a change log using [GitHub's releases][releases]
functionality. The format of the log is based on
[Keep a Changelog][keepchangelog].

Releases are based on [Semantic Versioning][semver], and use the format
of ``MAJOR.MINOR.PATCH``. In a nutshell, the version will be incremented
based on the following:

- ``MAJOR``: Incompatible or major changes.
- ``MINOR``: Backwards-compatible new features and enhancements.
- ``PATCH``: Backwards-compatible bugfixes and package updates.
