# retroarch-x86-linux
Retro Console, Retroarch, Debian, x86

This is just a general guide on how I plan to turn a tiny PC into a retro console.  I'll be using Debian and Retroarch.  I also want a good plan to backup retroarch config files, but that may come later.  I don't have time to go into super detail on everything like I did for my Raspberrypi Retroarch guide.  Mostly this is just for me, and a reminder of how to work on the system if something goes wrong.

Start out with a good minimal installation that's not too minimal. 

https://www.debian.org/distrib/

Choose the Xfce Live ISO.  I like Xfce because it's got an oldschool feel to it, and it's fairly minimal compared to KDE or GNOME.  During installation I noticed that some partition options can be different depending on if you chose to boot your thubdrive as EFI, so choose EFI.

clean up installation a little (optional)

```
sudo apt remove libreoffice-*
sudo apt autoremove
```
# Install Software
Install gamemode, my favorite command line editor, and flatpak.  Flatpak makes installing Retroarch very simple.
```
sudo apt install gamemode vim flatpak
sudo flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
```
After Flatpak is installed, reboot your computer.

To install packages from Flatpak go here:
https://flathub.org

But we want to focus mostly on installing Retroarch from Flatpak.  Do this:
```
flatpak install flathub org.libretro.RetroArch
```
And just so you know how to run Retroarch from a flatpak, here you go, but you may never need this:
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



--------------

I wanted to make sure I could quickly work on this retro system if something happens, so I divided the partions up like this:
```
/boot-efi
/root
/var
/home
```

The point of doing this is for a couple reasons.  The Flatpak apps are located in the /var, so if I run into a bad Debian update or sofware conflict, I can just use the USB Debian ISO to basically repair the system without losing any Flatpak's, which includes RetroArch.  Also, since my /home is separate, I won't lose any RetroArch config files or games.  I realize there are more modern ways of being able to manage a system, but I'm feeling nostolgic for Debian, and the old ways of doing things.  And for this system, those old ways are fine.

To restore the Debian system files, boot from the usb, install the system, but choose to do custom partitions.  And set them like this:
```
/boot-efi (format)
/root (format)
/var (keep data)
/home (keep data)
```
Be sure to set the boot flat for the /boot-efi partion.  After this is all set up, you'll just need to install Flatpak, but the Flatpak apps will all be there and functioning as they normally do.




aptitude install gamemode
then enable it in retroarch in Core > Latency
