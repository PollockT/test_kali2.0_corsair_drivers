---------------

#### Linux
Know your Keyboard type and Mouse Type!!

If you have problems connecting the device to your system (device doesn't respond, ckb-daemon doesn't recognize or can't connect it) and/or you experience long boot times when using the keyboard, try adding the following to your kernel's `cmdline`:

* K65 RGB: `usbhid.quirks=0x1B1C:0x1B17:0x20000408`
* K70: `usbhid.quirks=0x1B1C:0x1B09:0x0x20000408`
* K70 RGB: `usbhid.quirks=0x1B1C:0x1B13:0x20000408`
* K95: `usbhid.quirks=0x1B1C:0x1B08:0x20000408`
* K95 RGB: `usbhid.quirks=0x1B1C:0x1B11:0x20000408`
* Strafe: `usbhid.quirks=0x1B1C:0x1B15:0x20000408`
* Strafe RGB: `usbhid.quirks=0x1B1C:0x1B20:0x20000408`
* M65 RGB: `usbhid.quirks=0x1B1C:0x1B12:0x20000408`
* Sabre RGB Optical: `usbhid.quirks=0x1B1C:0x1B14:0x20000408`
* Sabre RGB Laser: `usbhid.quirks=0x1B1C:0x1B19:0x20000408`
* Scimitar RGB: `usbhid.quirks=0x1B1C:0x1B1E:0x20000408`

For instructions on adding `cmdline` parameters in Ubuntu, see https://wiki.ubuntu.com/Kernel/KernelBootParameters

If you have multiple devices, combine them with commas, starting after the `=`. For instance, for K70 RGB + M65 RGB: `usbhid.quirks=0x1B1C:0x1B13:0x20000408,0x1B1C:0x1B12:0x20000408`

If it still doesn't work, try replacing `0x20000408` with `0x4`. Note that this will cause the kernel driver to ignore the device(s) completely, so you need to ensure ckb-daemon is running at boot or else you'll have no input. This will not work if you are using full-disk encryption.

If you're using **Unity** and the tray icon doesn't appear correctly, run `sudo apt-get install libappindicator-dev`. Then reinstall ckb.


Common issues:
- **Problem:** ckb says "No devices connected" or "Driver inactive"
- **Solution:** Try rebooting the computer and/or reinstalling ckb. Try removing the keyboard and plugging it back in. If the error doesn't go away, try the following:
- **Problem:** Keyboard doesn't work in BIOS, doesn't work at boot
- **Solution:** Some BIOSes have trouble communicating with the keyboard. They may prevent the keyboard from working correctly in the operating system as well. First, try booting the OS *without* the keyboard attached, and plug the keyboard in after logging in. If the keyboard works after the computer is running but does not work at boot, you may need to use the keyboard's BIOS mode option.
- BIOS mode can be activated using the poll rate switch at the back of the keyboard. Slide it all the way to the position marked "BIOS". You should see the scroll lock light blinking to indicate that it is on. (Note: Unfortunately, this has its own problems - see Known Issues. You may need to activate BIOS mode when booting the computer and deactivate it after logging in).
- **Problem:** Keyboard isn't detected when plugged in, even if driver is already running
- **Solution:** Try moving to a different USB port. Be sure to follow [Corsair's USB connection requirements](http://forum.corsair.com/v3/showthread.php?t=132322). Note that the keyboard does not work with some USB3 controllers - if you have problems with USB3 ports, try USB2 instead. If you have any USB hubs on hand, try those as well. You may also have success sliding the poll switch back and forth a few times.

#### Reporting issues

If you have a problem that you can't solve (and it isn't mentioned in the Known Issues section below), you can report it on [the GitHub issue tracker](https://github.com/ccMSC/ckb/issues). Before opening a new issue, please check to see if someone else has reported your problem already - if so, feel free to leave a comment there.

Known issues
------------

- Using the keyboard in BIOS mode prevents the media keys (including mute and volume wheel), as well as the K95's G-keys from working. This is a hardware limitation.
- The tray icon doesn't appear in some desktop environments. This is a known Qt bug. If you can't see the icon, reopen ckb to bring the window back.
- When starting the driver manually, the Terminal window sometimes gets spammed with enter keys. You can stop it by unplugging and replugging the keyboard or by moving the poll rate switch.
- When stopping the driver manually, the keyboard sometimes stops working completely. You can reconnect it by moving the poll rate switch.

