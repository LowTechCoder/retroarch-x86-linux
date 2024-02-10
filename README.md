# retroarch-x86-linux
Retro Console, Retroarch, Debian, x86

This is just a general guide on how I plan to turn a tiny PC into a retro console.  I'll be using Debian and Retroarch.  I also want a good plan to backup retroarch config files, but that may come later.  I don't have time to go into super detail on everything like I did for my Raspberrypi Retroarch guide.  Mostly this is just for me, and a reminder of how to work on the system if something goes wrong.

Start out with a good minimal installation that's not too minimal. 

https://www.debian.org/distrib/

Choose the Xfce Live ISO.  I like Xfce because it's got an oldschool feel to it, and it's fairly minimal compared to KDE or GNOME.  During installation I noticed that some partition options can be different depending on if you chose to boot your thubdrive as EFI, so choose EFI.

clean up installation a little (optional)

```
sudo apt update
sudo apt upgrade
sudo shutdown -r now
sudo apt remove libreoffice-*
sudo apt autoremove
```
# Install Software
Install gamemode, my favorite command line editor, and flatpak.  Flatpak makes installing Retroarch very simple.
```
sudo apt install wget
sudo apt install gamemode vim flatpak
sudo flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
sudo shutdown -r now
```

After Flatpak is installed, reboot your computer.

To install packages from Flatpak go here:
https://flathub.org


But we want to focus mostly on installing Retroarch from Flatpak.  Do this:
```
flatpak install flathub org.libretro.RetroArch
```
I sometimes need to control my mouse with a controller so install antimicroX.
```
flatpak install flathub io.github.antimicrox.antimicrox
```
Enable Gamemode in Retroarch with Core > Latency

Run PCSX2 in fullscreen and bigpicture mode:
```
flatpak install flathub net.pcsx2.PCSX2
flatpak run net.pcsx2.PCSX2 -bigpicture -fullscreen
```

I may start using a program launcher instead of booting straigt up to RetroArch:
https://github.com/complexlogic/flex-launcher


I also set up in Xfce settings startup, this command to auto run Retroarch(DOUBLE CHECK THIS)
```
flatpak run org.libretro.RetroArch
```
# Desktop Settings

Set your WIFI by clicking the top right icon that looks like 2 tiny screens.

And you may want to set the display resolution at 1080p since that is our target for good looking emulation that doesn't require a ton of video card power.
Applications > Settings > Display

The monitor kept wanting to change screen sizes on me for xfce4, everytime I flipped monitors to the mac.  So i found a setting to fix that
Settings > Display > Advanced Tab > When new displays are connected = Do Nothing

You may also want to disable all sleeping options in Xfce > Power


I have noticed that sometimes these settings can be lost after a reboot.  Just do it again and try again.  I think the most I ever had to do this was 3 times.



I wanted to make sure I could quickly work on this retro system if something happens, so I divided the partions up like this:
```
/boot/efi - 300mb
/root - 20gb
/var - 21gb
/home - largest
```

The point of doing this is for a couple reasons.  The Flatpak apps are located in the /var, so if I run into a bad Debian update or package conflict, I can just use the USB Debian ISO to  repair the system without losing any Flatpak's, which includes RetroArch.  Also, since my /home is separate, I won't lose any RetroArch config files or games.  I realize there are more modern ways of being able to manage a system, but I'm feeling nostolgic for Debian, and the old ways of doing things.  And for this system, those old ways are fine.

Format /boot/efi as fat32, and the rest is ext4

To restore the Debian system files, boot from the usb, install the system, but choose to do custom partitions.  And set them like this:
```
/boot/efi (format as fat32)
/root (format)
/var (keep data)
/home (keep data)
```
Be sure to set the boot flag for the /boot-efi partion.  After this is all set up, you'll just need to install Flatpak, but the Flatpak apps will all be there and functioning as they normally do.



