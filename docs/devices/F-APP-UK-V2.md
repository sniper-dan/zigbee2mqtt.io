---
title: "SmartThings F-APP-UK-V2 control via MQTT"
description: "Integrate your SmartThings F-APP-UK-V2 via Zigbee2mqtt with whatever smart home
 infrastructure you are using without the vendors bridge or gateway."
---

*To contribute to this page, edit the following
[file](https://github.com/Koenkk/zigbee2mqtt.io/blob/master/docs/devices/F-APP-UK-V2.md)*

# SmartThings F-APP-UK-V2

| Model | F-APP-UK-V2  |
| Vendor  | SmartThings  |
| Description | Zigbee Outlet UK with power meter |
| Supports | on/off, power measurement |
| Picture | ![SmartThings F-APP-UK-V2](../images/devices/F-APP-UK-V2.jpg) |

## Notes

## Pairing
Plug in the outlet whilst holding either one of the switches on the side. Release when the blue light begins to flash. After this the device will automatically join.

## Manual Home Assistant configuration
Although Home Assistant integration through [MQTT discovery](../integration/home_assistant) is preferred,
manual integration is possible with the following configuration:


{% raw %}
```yaml
switch:
  - platform: "mqtt"
    state_topic: "zigbee2mqtt/<FRIENDLY_NAME>"
    availability_topic: "zigbee2mqtt/bridge/state"
    payload_off: "OFF"
    payload_on: "ON"
    value_template: "{{ value_json.state }}"
    command_topic: "zigbee2mqtt/<FRIENDLY_NAME>/set"

sensor:
  - platform: "mqtt"
    state_topic: "zigbee2mqtt/<FRIENDLY_NAME>"
    availability_topic: "zigbee2mqtt/bridge/state"
    unit_of_measurement: "W"
    icon: "mdi:flash"
    value_template: "{{ value_json.power }}"

sensor:
  - platform: "mqtt"
    state_topic: "zigbee2mqtt/<FRIENDLY_NAME>"
    availability_topic: "zigbee2mqtt/bridge/state"
    icon: "mdi:signal"
    unit_of_measurement: "lqi"
    value_template: "{{ value_json.linkquality }}"
```
{% endraw %}


