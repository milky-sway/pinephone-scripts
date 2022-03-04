# pinephone-scripts
Helper scripts for PinePhone and PinePhone Pro users

## sleepwalk
"Proof-of-concept" bash script to periodically wake up the phone to check web-based notifications (such as messenger or e-mail notifications). The goal of this is to get a better battery time while still being able to receive web-based notifications. Currently, only calls and SMS will make the phone wake up, when deep sleep is used.

By default, the script will make the phone sleep within 60 seconds, when the screen is turned off (sleep mode will not apply while the screen is on and will make the phone sleep for 30 seconds for the first time (if not interrupted by pressing the power button to wake the phone). It will then keep the phone awake for 30 seconds and, as long as the user does not interact with the device, put the phone immediately back to sleep mode for a longer time, in 30-second steps, up to a maximum of 10 minutes. If the screen is turned on, sleep time will reset to the initial value. You can change the durations directly at the top of the script. While the phone is sleeping, the RGB LED will light up constantly green and when it is awake for the short period of time, it will be a blinking red. The LED will be turned off, when the phone screen is enabled (for example by pressing the power button).

Howto install and use:
- Save the 'sleepwalk' script to /usr/local/bin and the systemd service file 'sleepwalk.service' to '/etc/systemd/system/'
- Disable deep sleep in your desktop managers settings such as phosh
- Execute 'systemctl enable sleepwalk.service' and 'systemcl start sleepwalk.service' to enable and start the service

Known issues:
- Phone will go to sleep even if apps like for example a music player is playing in the background while the screen is turned off. It will however not sleep, if you are making a call.

Dependencies:
- rtcwake
