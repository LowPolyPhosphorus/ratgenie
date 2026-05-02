![ratgenie](images/ratgenie.png)
 
# ratgenie
ratgenie, my solution to the insufferable thing known as a garage door opener. (specifically, Genie/MyQ/Chamberlain/LiftMaster/Raynor/Craftsman/Clicker garage door openers) similar to the ratgdo (rage against the garage door opener) the ratgenie will fix hopefully at least the MachForce Genie Garage Door Opener (new name, ratmfggdo, rolls off the tongue doesn't it?)

## what is this?
ratgenie is a locally controlled, no subscription, no cloud, no nonsense garage door controller built on an ESP32-WROOM. it wires directly into your garage door opener's wall button terminals and gives you full open/close/status control through Home Assistant over WiFi via ESPHome. no MyQ account. no Aladdin Connect. no $5/month to open your own garage door.

## why does this exist?
because Genie/Chamberlain decided that you need a paid subscription to open your own garage door with your own phone on your own wifi network. the MachForce Connect has Aladdin Connect built in, which used to work fine, then stopped pairing after a new motor install and the only fix was apparently paying for a subscription. ratgenie is the fix.

inspired by [ratgdo](https://github.com/PaulWieland/ratgdo) by Paul Wieland, which does the same thing for Security+ 2.0 Chamberlain/LiftMaster openers. ratgenie targets Genie's dry contact interface since the MachForce doesn't use Security+ 2.0.

## what does it do?
- opens and closes your garage door from Home Assistant
- detects door open/closed state using an HC-SR04 ultrasonic sensor mounted on the ceiling (soon to be replaced by ESP32 and MCU-6050 project)
- triggers the door by momentarily shorting the wall button terminals through a relay, exactly like pressing the button yourself
- runs on ESPHome, so Home Assistant autodiscovers it over MQTT with zero configuration

## hardware
- ESP32-WROOM
- HC-SR04 ultrasonic distance sensor
- 5V single channel optocoupler relay module
- some wire

## bill of materials
| part | quantity | link |
|------|----------|------|
| ESP32-WROOM | 1 | owned |
| HC-SR04 ultrasonic sensor | 1 | owned |
| 5V single channel optocoupler relay module | 1 | [aliexpress](https://www.aliexpress.us/item/3256806393437087.html) |

## tested on
- Genie MachForce Connect Model 4063-TNMSV

## not tested on
literally everything else. if you make it and it works on your opener, open an issue and let me know and i'll add it to the list.

## credits
- [ratgdo](https://github.com/PaulWieland/ratgdo) by Paul Wieland for the concept and inspiration
- [ESPHome](https://esphome.io/) for making this not a nightmare to implement
## Gallery

<img src="https://stasis.hackclub-assets.com/images/1775941044733-2rdv6r.png" alt="image"/>
<img src="https://stasis.hackclub-assets.com/images/1775941635940-lhmqtl.png" alt="image"/>
<img src="https://stasis.hackclub-assets.com/images/1775786781729-6zog70.png" alt="image"/>
<img src="https://stasis.hackclub-assets.com/images/1775942244002-s1wxlb.png" alt="image"/>

> ^^ your physical button should look like this in the back for this to work (two screw posts) ^^

<img src="https://stasis.hackclub-assets.com/images/1775945220615-biijak.png" alt="image"/>
<img src="https://stasis.hackclub-assets.com/images/1775944886375-aou5ls.png" alt="image"/>
