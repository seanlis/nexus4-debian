# Installing Debian sid on Nexus 4
1. Put device in developer mode (if not done already), see for example:
  * http://www.androidcentral.com/how-enable-developer-settings-android-42
  * then `sudo fastboot oem unlock` from fastboot menu
2. Install adb plus fastboot
3. Reboot device, hold down volume-down key to get to fastboot screen
  * or `adb reboot bootloader`
4. At fastboot screen, `fastboot boot boot/mako-boot.img`
  * This will not flash this kernel, so next time you reboot you are back to your original kernel.
5. Run `adb push rootfs/ /data`
6. Run `adb push busybox /data`
7. Connect to device: `adb shell`, `cd /data`
8. On device, extract files: `cat sid-armhf.tar.gz_a* |./busybox tar xvz`
9. Stop android UI and start chroot: `stop`, `/data/sid/start-chroot.sh`, `./enter-chroot.sh`
10. start X: `LD_LIBRARY_PATH=/usr/local/lib Xorg :0`, `DISPLAY=:0 LD_LIBRARY_PATH=/usr/local/lib fluxbox`
11. install anything else you need with `apt`, add users `adduser`, ...

## NOTES:
for more information, refer to: https://github.com/freedreno/nexus4-fedora
