# Configuration

All configuration is done through `firmware/ratgenie.yaml` and `firmware/secrets.yaml`.

## secrets.yaml

| Key | Description |
|-----|-------------|
| `wifi_ssid` | Your WiFi network name |
| `wifi_password` | Your WiFi password |
| `api_encryption_key` | Base64 encryption key for Home Assistant API |
| `ota_password` | Password for over the air firmware updates |
| `fallback_password` | Password for the fallback hotspot if WiFi fails |

## GPIO Pins

| Pin | Function |
|-----|----------|
| GPIO13 | HC-SR04 trigger |
| GPIO12 | HC-SR04 echo |
| GPIO26 | Relay control |
| GPIO2 | Status LED |

These can be changed in `ratgenie.yaml` if your wiring differs.

## Distance Threshold

The ultrasonic sensor determines door state based on a distance threshold set in the `on_value` block:

```yaml
sensor.in_range:
  id: garage_distance
  above: 1.0
```

`above: 1.0` means anything over 1 meter is considered open. Adjust this based on your ceiling height. Mount the sensor on the ceiling pointing down at the door panel when closed the door will be close to the sensor, when open the sensor will see all the way to the floor.

## Relay Pulse Length

The relay closes for 500ms by default to simulate a button press:

```yaml
- switch.turn_on: door_relay
- delay: 500ms
- switch.turn_off: door_relay
```

If your opener does not trigger reliably, try increasing this to 750ms or 1000ms.

## Status LED

The status LED on GPIO2 blinks every 5 seconds when WiFi is connected and stays solid when disconnected. The check interval can be changed here:

```yaml
interval:
  - interval: 5s
```
