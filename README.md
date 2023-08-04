# retroarch-x86-linux
Retro Console, Retroarch, Debian, x86

I have other guides to building a retro console with a Raspberry Pi, but I'm bored and I want a little more power, so I may can squeeze in Gamecube and possibly eventually PS2 emulators.  So I'll start with this guide on my big AMD PC, and eventually over time, choose a good tiny PC to move all this to, and I'll list all that hardware and controller I use, along with how to set up everything.  One thing that sets my builds apart from the normal is I have an auto running script that backs up the config files of Retroarch, so I'll be setting that up to.  Follow along, more to come.

Start out with a good minimal installation that's not too minimal. 
https://www.debian.org/distrib/
So choose the live installer iso.  Get it onto a thumbdrive.  During installation it will ask you what Desktop to use, choose XFCE.  I like XFCE because it's got an oldschool feel to it, and it's fairly minimal compared to KDE or GNOME.  My auto boot scripts depend on Xfce being installed.


clean up installation a little (optional)
```
sudo aptitude remove libreoffice-math libreoffice-impress libreoffice-draw libreoffice-core libreoffice-common libreoffice-writer libreoffice-math libreoffice-impress libreoffice-draw libreoffice-core libreoffice-common libreoffice-calc goldendict
```
or 

```
sudo apt remove libreoffice-*
sudo apt autoremove
```




--------------
If you install retroarch with apt, you'll need to go into the retroarch menu and get the controller working like this:
Main Menu > Online Updater > Update Controller Profiles

Don't ever use "default config" in retroarch because it will kill all the font things.

Download Cores wasn't showing up so I had to enable it in the retroarch config
menu_show_core_updater = "true"

the monitor kept wanting to change screen sizes on me for xfce4, everytime I flipped monitors to the mac.  So i found a setting to fix that
Settings > Display > Advanced Tab > When new displays are connected = Do Nothing

while installing flatpack, it wanted to install some gnome helper package but I skipped it.  You can just find software at flathub and click the button beside the software to do a command install

I started off with using aptitude
Install this for autocomplete
sudo aptitude install bash-completion
restart terminal

aptitude install gamemode
then enable it in retroarch in Core > Latency
