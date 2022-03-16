# About

This is just some config files and tips for my modded Ender 3 V2 (SKR Pico + Klipper + LGX)


# Stuff for the Raspberry Pi

Add `dtoverlay=pi3-miniuart-bt` to the upper most part of `/boot/config.txt` so that serial connection to the SKR Pico works

Use `fish://pi@192.168.37.3/` in Dolphin to connect to the Pi

# Stuff for SKR Pico

## Endstops

The endstops on the SKR Pico board have three pins each: io pin, gnd, 5V. you need to connect the endstop switches to pin and gnd. The 5V you can ignore

# Stuff for Klipper

## BL Touch

I use an original BL Touch 3.1. Older versions or clones might need different configs

Check if BL Touch Pin moves up and down:

```
BLTOUCH_DEBUG COMMAND=pin_down
BLTOUCH_DEBUG COMMAND=pin_up
```

Check if it is triggering correct:

```
bl tough should be red
BLTOUCH_DEBUG COMMAND=pin_down
pin should be down and no light
BLTOUCH_DEBUG COMMAND=touch_mode
QUERY_PROBE
result should read "open"
move the pin carefully up until red light goes and and hold it there with one hand (if it fully retracts you pushed too far). use other hand to send another:
QUERY_PROBE
result should read "triggered"
remove finger
pin should be down and red light should be off
QUERY_PROBE
result should read "open"
BLTOUCH_DEBUG COMMAND=pin_up
```

# Links

* [Example Klipper config - SKR Pico](https://github.com/Klipper3d/klipper/blob/master/config/generic-bigtreetech-skr-pico-v1.0.cfg)
* [Example Klipper config - Ender 3 V2](https://github.com/Klipper3d/klipper/blob/master/config/printer-creality-ender3-v2-2020.cfg)
* [SKR Pico - Pinout](https://github.com/bigtreetech/SKR-Pico/blob/master/Hardware/BTT%20SKR%20Pico%20V1.0-PIN.pdf)
* [SKR Pico - Manual](https://github.com/bigtreetech/SKR-Pico/blob/master/BTT%20SKR%20Pico%20V1.0%20Instruction%20Manual.pdf)