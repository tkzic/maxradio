README.md 
maxradio: Max/MSP SDR project and tutorials
Jan 23, 2015
http://zerokidz.com/radio
local: maxradio

#### email: tkzic@megalink.net

----------------------------------

(yet another) Interim upgrade of Mac OS Max version.

Windows, runtime, standalone, documentation upgrades still in progress...

### changes 1/23/2015

The soft66lc driver in MacOS has been broken since Mavericks. Mac OS is hijacking the device. A temporary fix is described here: [link](http://reactivemusic.net/?p=18273) 

Essentially just unload the apple driver from the command line before running Max: sudo kextunload -bundle com.apple.driver.AppleUSBFTDI

### changes 5/31/2014

added new drivers.

driver for rtl-sdr
minor bug fixes

instructions

Open maxsdr7a.maxpat in Max

#### Previous version of README...

--
2013: Just a quick update:
I have not been able to update the archive recently. But there are minor bug fixes coming.
And a driver for the FCDPRO+ for Mac. Although I can't recommend FCDPRO+ due to audio sync
issues. email me if you have questions. tz

--------------------------------------

Latest test reports:

Max5 - ok
Max6 - ok

MacOS 10.6 & 10.7 (intel32 & 64bit) - ok
MacOS 10.6 PPC - ok 

Windows7 (32bit and 64bit) - ok

------------------------------------
version: maxsdr7a (Mac OS & Windows)

------------------------------------
This project is available as a zipped archive file (.zip)



NOTE: tutorial patches are now in the maxradio folder. Tutorial documents are in the 

maxradio/docs/ folder. Or… you can download tutorials separately using the
tutorials link at http://zerokidz.com/radio. If you download them separately, everything
you need to run the tutorials is in that one folder, including drivers, libraries, etc.,
Tutorials should work with the runtime version. 

2) Note: If you are using the Runtime version of Max you can now change audio settings
by double-clicking the green "audioSettings" object in the lower right corner of the 
screen, next to the "audio on/off" button. 

3) Check online documentation for help on how to use the program 
http://zerokidz.com/radio

4) The FUNCube, and any other audio devices, and virtual audio devices, need
to be plugged in or running before launching Max - otherwise Max won't find them.

5) Sample rate should be set to 96k or higher for best audio quality and bandwidth. 
(double-click the green "audioSettings" object in the lower right corner of the 
screen, next to the "audio on/off" button). 

6) The name of the file to run is:

	maxsdr7a.maxpat 
	
If you can't find that file look for a newer version with a higher letter of
 the alphabet, for example, maxsdr7b.maxpat

NOTE: The very first time you run this patch in Windows you may get a warning 
about the Firewall. Max uses ports 7400 (receive from touchOSC) and 7402 (send
to touchOSC) are used for communication with touchOSC over your local/wireless network.

------------------------------------------------------------------
Tutorial patches and documentation are in the tutorial folder. If you move them
somewhere else, you'll still need to have the maxsdr5 folder (described above) in
your max user filepath - because the maxsdr5 folder contains patches and externals
required by the tutorials.

-------------------------------------------------------------------
known issues:

-------------------------------------------------------------------
- Please read the user manual - maxsdr5.pdf. Access it online:
http://zerokidz.com/radio/docs/maxsdr5.pdf
Or from the maxsdr5/docs/ folder. Its getting better all the time…

- Occasional audio problems have been observed with Max6 - including 
crackling, high CPU usage, or no audio at all. If this happens, try 
restarting Max. If nothing else works you may want to consider using Max5 until 
Max6 becomes more stable.

- There are problems with running FUNCube and Soft66lc2 at the same time. Switching
from one device to the other seems to make the Soft66lc2 stop working. Workaround: Run the 
devices separately.

- If setting frequency on either device just stops working. Or you get error 
messages in the Max window whenever you change frequency - try reloading the patch
or restarting Max.

- The FUNCube needs firmware 18f (18.06) or greater to work with this program.
We use the same drivers as QTHid. Firmware updates are available at the FUNCube 
website.

- Sometimes loud buzzing occurs when you first toggle audio on - This has happened
on the Macbook Pro.  If it does happen, it may swamp the AGC and filters - leaving
you wondering why nothing works. Just close the patch and reload it.

- If you hear crackling that isn't radio noise, or periodic buzzing (comb filtering)
especially in FM mode, increase the signal vector size in Options : DSP Status 
(Audio Status in Max6).  Try values of 512, 1024, or 2048 until the problem goes
away or gets less annoying. I use 512 on a MacBook Pro. Note: You can also 
change audio settings by double-clicking the green audioSettings object (lower right
corner)

- Sometimes the left/right arrow keys (to change frequency) don't work. This happens when
you click on an object, like a gain slider, that takes control of the arrow keys
for its own personal use. Workaround: click anywhere in the whitespace of the patch.
Then try the arrow keys again. We're working on an alternative…  

- Collective and standalone versions are temporarily unavailable, but you can
make your own collectives using the supplied scripts: maxsdr5c_collective_script.txt
(Mac OS) and maxsdr_collective_script_win.txt (Windows). Copy the file: presets.json
to the folder where you're running the collective. Hopefully the collectives will
return soon!


##### If you are Missing soft66lc2 libraries: (see below for solution).

 
-----------------------------
Here are the instructions for installing Soft66lc2 library files. If the
Soft66lc2 isn't working please read this first.

----------------------------------------------
Soft66lc2 library files for max radio project:
----------------------------------

------------
MacOS (For Windows see below)
----------------------------------------------
Several dynamic library files are required for the Soft66lc2 device control external
object to load properly in Max/MSP.  If the Max radio patch loads and runs without
errors, your computer already has the necessary library files installed. You can safely
ignore these instructions.

On the other hand‚Ä¶ if you load the max radio patch and see error messages in the Max
window something like:

	sfctrl: unable to load object bundle executable
 	2011-11-11 15:51:06.328 MaxMSP[25680:507] Error loading /Users/tkzic/maxsdr5/sfctrl.mxo/Contents/MacOS/sfctrl:
	dlopen(/Users/tkzic/maxsdr5/sfctrl.mxo/Contents/MacOS/sfctrl, 262):
	Library not loaded: /usr/local/lib/libftdi.1.dylib
	Referenced from: /Users/tkzic/maxsdr5/sfctrl.mxo/Contents/MacOS/sfctrl
	Reason: image not found

Then you've come to the right place. 

First - If your computer has the PPC (PowerPC) chipset there is now hope! The maxradio/ppc/ folder
has libraries, a special max external object - with instructions in maxsdr5/ppc/READMEppc.txt,
Read the instructions and then come back here using the PPC versions of the library 
files instead of the ones in the maxradio/lib/ folder…

 
To get the soft66lc2 running you'll need to install libftdi on your computer.
Libftdi is an open source library of USB drivers required by the Max external. 
There are two ways to do this. 

1) (the hard way) Install libraries by downloading and compiling source. Use instructions in this link:

	http://geckodownloads.googlecode.com/files/libftdimacosx.pdf


2) (or the easy way) Just copy the library files from the maxsdr5/lib folder to the correct location
on your computer using the instructions below. These libraries are 'fat' binaries and will work
on both 32 & 64 bit architectures.

----------------------------------------------------------
Instructions for copying libftdi library files:
-----------------------------------------------------------

Short version: Copy all of the .dylib files in the maxsdr5/lib directory to: /usr/local/lib

Detailed version:

You'll be typing commands into the terminal console. Terminal is in the Applications/Utilities folder.
You'll need your admin password for some of the commands. Just enter it when prompted.

1. See if /usr/local/lib exists. Type:

	ls -l /usr/local/lib

If the response is: "No such file or directory" then create it by typing:  

	sudo mkdir /usr/local/lib

2. To copy the files, first go the maxsdr5/lib folder. (assuming its under your home user
folder - otherwise substitute correct folder location for "maxsdr5/lib")

	cd maxsdr5/lib

3. Then copy all the library files:

	sudo cp *.dylib /usr/local/lib

4. Now quit terminal. Return to Max/MSP and reload maxsdr5c.maxpat   

-------------
Windows 
-------------
If you're using the soft66lc2 in Windows, you'll need to copy the ft2dxx.dll file from
the lib/ folder to the folder containing the Max program:

	c:\ProgramFiles\Cycling'74\Max5.0\   (for Max5)
	c:\ProgramFiles\Cycling'74\Max6.0\ 	(for Max6)

Alternatively You could copy it to the Windows\system32 or 
Windows\system64 directory. But I'm not sure why you would want to do that.

The system may give you warnings about privileges - please ignore them and forge on through.

-------------------------------------------------------------------------------------------
Problems? Questions? Ideas? Interested in developing?  Send email to tkzic@megalink.com

#### Tom Zicarelli, KA1IS
--------------------------------------------------------------------------------------------
This project was derived from the works of the following developers.

* Kazunori Miura, JA7TDO - hardware and software design of soft66lc2
* Thomas Horsten - Linux soft66add control software
* Thomas Robin-Couerrier - ppc Max external software and library conversion & testing
* Howard Long, G6LVB - hardware and software design of FUNCube
* Alexandru Csete, OZ9AEC - QTHid FUNCube control software
* Mario Lorenz, DL5MLO - FUNCube control software
* David Pello, EA1IDZ - Linux FUNCube command line control software.
* Joseph Zicarelli, KB1URI - design, technical advice, and testing.

Thank you!





 