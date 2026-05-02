# Installation

## Requirements

- ESP32-WROOM
- ESPHome CLI (`pip install esphome`)
- Home Assistant with ESPHome integration

## Flashing

1. Clone the repo
2. Copy `firmware/secrets.yaml.example` to `firmware/secrets.yaml` and fill in your WiFi credentials and keys
3. Generate an API encryption key by running this in PowerShell:
```powershell
   [Convert]::ToBase64String((1..32 | ForEach-Object { [byte](Get-Random -Max 256) }))
```
4. Run `esphome run firmware/ratgenie.yaml` from the repo root
5. Select the COM port when prompted

## Home Assistant

Once flashed and on your network, Home Assistant will autodiscover ratgenie automatically. Go to Settings > Devices & Services and accept the ESPHome notification. Enter your API encryption key from secrets.yaml when prompted.

## Wiring

See [wiring diagram](../images/wiring.svg) for full wiring details. The relay COM and NO terminals wire in parallel with your existing wall button terminals on the opener.

## Notes

- PlatformIO cannot handle spaces in file paths on Windows. Keep the firmware folder at a path with no spaces like `C:\firmware`
- GPIO12 and GPIO2 are strapping pins and will show warnings during compile, this is expected and safe to ignore
- The ultrasonic sensor is optional for v1, the cover entity uses optimistic mode by default
- A custom built tilt and acceleration sensor for direct integration into the ratgenie is in the works! (ultrasonic sensor may be deprecated because it is overly complicated to wire it all the way to the door from the button)
