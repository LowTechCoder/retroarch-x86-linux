# retroarch-x86-linux
Retro Console, Retroarch, Debian, x86

I have other guides to building a retro console with a Raspberry Pi, but I'm bored and I want a little more power, so I may can squeeze in Gamecube and possibly eventually PS2 emulators.  So I'll start with this guide on my big AMD PC, and eventually over time, choose a good tiny PC to move all this to, and I'll list all that hardware and controller I use, along with how to set up everything.  One thing that sets my builds apart from the normal is I have an auto running script that backs up the config files of Retroarch, so I'll be setting that up to.  Follow along, more to come.

clean up installation a little (optional)
```
sudo aptitude remove libreoffice-math libreoffice-impress libreoffice-draw libreoffice-core libreoffice-common libreoffice-writer libreoffice-math libreoffice-impress libreoffice-draw libreoffice-core libreoffice-common libreoffice-calc goldendict
```
or 
```
sudo apt remove libreoffice-*
```
