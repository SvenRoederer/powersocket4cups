# powersocket4cups

This project was started to power on and off a printer automatically when a printjob has to be printed. It started years ago when I still had 
my old HP LaserJet III and got my hands onto a Gembird "Silver Shield Programmable Power Outlet Strip" (SIS-PM). 
This old printer seemed to come from a time, when saving energy was not considered important  and so there was always my fight between 
"turning off to save electrical power" and "being to lazy / to sleepy to walk over an turn off". So the 1st solution was a wrapper-script 
around the lp-command to turn on the printer, when a job get's in and using a cronjob to turn it off, after some time of inactivity. Thanks to 
[sispm](https://sourceforge.net/projects/sispm/) and [sispmctl](https://sourceforge.net/projects/sispmctl/) (https://github.com/xypron/sispmctl)
it was a nice way to control the 4 sockets from the commandline.

This setup work acceptable well, but was still very hacky And I was always planning to patch the lpr-package to include native support, but 
patching and recompiling on every update of the package always stopped me to do so. When CUPS became more public I found that its backends 
offer moch more flexibility for squeezing in such functionality.
So I started to modify my shell-wrapper for lpr into a CUPS backend.

## CUPS backends for the Gembird SIS-PM

Based on the sispmctl tool the 1st version of a CUPS-backend was done. The oldest commit to my local Subversion-repo points to early 2012, but 
that's not the inital version used at all.
The last change to the code was made in Aug 2013 and sometime after this the SIS-PM brcame unusable as of the broken internal mechanics holding 
the conductor-rails in place (https://www.hardwareecke.de/testberichte/sonstiges/silvershieldsteckd1.php).
I remember a time, when I had my LasterJet (not the old Lasterjet III anymore) and a Epson LQ-850 connected (for some continuous form paper label
printing) also.

## CUPS backend for Edimax Smartplug SP-1101W

After having to life without automatic printer powering for some time I spotted the Edimax SmartPlug as a good successor of the SIS-PM. The Edimax
socket-adapter provides WiFi-connectivity via TCP/IP for a single socket. As I had no demand for a 2nd printer anymore, this was a ideal replacement
of the SIS-PM requiring no USB-cabling and consuming less power (the SIS-PM was specified with 15 watts).
I made a fork of the SIS-PM shell backend and soon converted to Python to directly utilize the [ediplug-py](https://github.com/wendlers/ediplug-py).
At sometime end 2019 / early 2020 the Edimax stopped working as of a bad capacitor in the internal power-supply section and I took it out of service
for a quick repair (by the end of 2021 it'S still waiting in my queue ...).

## CUPS backend for Delock 11827 powersocket

Being at the local electronics shop I found this power-socket family made by Delock which is using the firmware of the [Tasmota](https://tasmota.github.io)
project. I bought a 11827 and 11826 as a replacement for the Edimax ....
