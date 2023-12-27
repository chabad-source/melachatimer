[![Melacha Timer Banner](https://github.com/chabad-source/melachatimer/blob/main/images/Melacha%20Timer%20Banner.png)](https://github.com/chabad-source/melachatimer)

[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)](http://makeapullrequest.com)
[![Codacy Badge](https://app.codacy.com/project/badge/Grade/f17caa6e3d2946378de9beae9fc0ffe8)](https://www.codacy.com/gh/chabad-source/melachaplug/dashboard?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=chabad-source/melachaplug&amp;utm_campaign=Badge_Grade)
[![Donate](https://img.shields.io/badge/Donate-PayPal-green.svg)](https://www.paypal.com/donate/?hosted_button_id=Q9A7HG8NQEJRU)

# Melacha Timer
A [Melacha](https://www.chabad.org/95906/) aware version which knows when it's [Shabbos](https://www.chabad.org/633659/) or [Yom Tov](https://www.chabad.org/holidays/default_cdo/jewish/holidays.htm).

This project is using [ESPHome](https://esphome.io/).

Looking to disable a smart doorbell for Shabbos?
Worried about Google or Alexa accidentally triggering on Shabbos or Yom Tov?
The solution is here!

## Features
-   [x] Smart: It features a full Jewish calendar on board, not just for Shabbos, but also for Yom Tov!
-   [x] Failsafe: Buttons are disabled on Shabbos and Yom Tov for added security.
-   [x] Intelligent: It automatically detects your location and provides the option to further customize.
-   [x] Aware: A LED flash lets you know when Shabbos mode is enabled.
-   [x] Local: All logic is processed on board.
-   [x] Adaptable: All code is open source, allowing for easy tweaking, correction, and expansion.
-   [x] Easy: Simply plug and play, and you're all set!

![Web Server Screenshot 1](https://github.com/chabad-source/melachatimer/blob/main/images/Web%20Server%20Screenshot%201.png)
![Web Server Screenshot 1](https://github.com/chabad-source/melachatimer/blob/main/images/Web%20Server%20Screenshot%202.png)

## Getting Started

### What You'll Need
-   A plug with ESPHome or Tasmota software installed.
-   Pre-flashed plugs can be bought from the [Athom](https://www.athom.tech/) or [Cloud Free](https://cloudfree.shop/) shop. There is also some preflashed plugs to be found on [Ebay](https://www.ebay.com/sch/i.html?_nkw=preflashed+smart+plug), and [Amazon](https://www.amazon.com/s?k=KAUF+Esphome).

## Installation

### Pre-configured

*Limitations*
-   Timezone is locked to EST unless you flash it yourself.
-   Your location won't be 100% accurate (you can update it via the web UI). 

*Setup*
-   Download the melachaplug.bin file from above. (currently none are compiled)
-   If your device is using Tasmota, follow instructions on how to upgrade from the [ESPHome docs](https://esphome.io/guides/migrate_sonoff_tasmota.html) or [Tasmota docs](https://tasmota.github.io/docs/Upgrading/#upgrade-using-webui).
-   If your device is using ESPHome, use the web UI to install the firmware.
-   Once the firmware is installed it will create a WiFi access point called "Melacha Plug Fallback", connect to it using any phone or computer.
-   On the devices webpage enter in your WiFi details (it should pop up, if it doesn't then it can be accessed via it's IP).
-   The device will restart, and should appear on your WiFi network.

### Custom Configuration
-   Set up your own ESPhome instance. If you have [Home Assistant](https://www.home-assistant.io/) then use the [ESPHome Dashboard](https://esphome.io/guides/getting_started_hassio.html), otherwise follow the [Command Line Interface](https://esphome.io/guides/getting_started_command_line.html) guide.
-   Find the YAML file for your device from the esphome folder above.
-   Configure the YAML settings to your liking, and flash device (more details on the ESPHome site).


## Usage

*first time setup*
-   Use "Detect Location" to auto detect your current location or put in your Latitude and Longitude manually.
-   Set the degree Shaboos/Yom Tov starts and ends. Default to "-0.833" (sunset) for start and "-8.5" (Alter Rebbe Tzeis) for the end.
-   Set early Shabbos if you execept in shabbos early. (it's hard coded to use Alter Rebbe Plag, use the offset feature to adapt).
-   Those in Eretz Yisroel select "Eretz Yisrael".

*timer configuration*
-   Select - Use this dropdown to select a timer to adjust a timers settings.
-   Enabled - Sets the timer as active.
-   Mode - When set to '0' it uses the time put into the "Time Hour" and "Time Minute". '1' uses sunrise. '2' uses sunset. '3' uses on a regular day tzeis, on a day before Shabbos or Yom Tov it uses the Shabbos Start time and on the last day of either Shabbos or Yom Tov it uses Shabbos End time.
-    Time Hour - Set the timer hour (Mode needs to be set to 0).
-    Time Minute - Set the timer minute (Mode needs to be set to 0).
-    Repeat - When disabled timer runs once when enabled it follows the rules set in the next toggles.
-    Sunday-Saturday - Select it based on the days of the week you'd like the timer to repeat.
-    Day Before Shabbos Or Yom Tov - Use this toggle to set timers for the day before Shabbos or Yom Tov (in addtion to whatever days of the week is set).
-    Day Of Shabbos Or Yom Tov - Any day which is either Shabbos or Yom Tov.
-    Last Day Of Shabbos Or Yom Tov - Just the last day (goes based on if the next day melacha is permitted).
-    Output - if you have mutiple switches or plugs running off one device this will set which one the timer is being used for (counting starts from 0).
-    Action - Sets what you want the relay to do '0' = turn off, '1' = turn on, '2' = toggles the relay.
-    Offset Hour-Minute - Set the offset time before (see "Negative Offset") or after the time set.
-    Negative Offset - Set the offset to be before the set vs after.

*other setup*
-   On the top there is "Relay 1 (Plug)" which is how to manually set the state of the plug/switch.
-   Use "Timer Override All" to override the timers settings and have the relay stay in the position you set it.

## Advanced

### Using Relays
You can customize this project for any sort of relays, including the sonoff basic. 

### Shabbos Mode
Shabbos from this project can be reused to be helpful in all types of projects.

### Potential Use Cases
-   Those with motion based lights, can have the motion disabled on Shabbos and Yom Tov.
-   Preserve energy usage during Shabbos and Yom Tov, for example of water heaters (temperature should be kept above °120F to prevent [Legionnaires’ disease](https://www.cdc.gov/legionella/wmp/control-toolkit/potable-water-systems.html)).
-   Turn off security cameras.
-   Disable accidental light switch triggers on Shabbos and Yom Tov (advanced).
-   Turn on a hot water urn before Shabbos and have it auto turn off after.
-   Disable a dishwasher so it won't accidentally get turned on.


## Contribute 

[![paypal](https://www.paypalobjects.com/en_US/i/btn/btn_donateCC_LG.gif)](https://www.paypal.com/donate/?hosted_button_id=Q9A7HG8NQEJRU) - or - [!["Buy Me A Coffee"](https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png)](https://www.buymeacoffee.com/rebbepod)
