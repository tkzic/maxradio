README.txt for Max/MSP radio project
November 15, 2011
http://zerokidz.com/radio
------------------------------------
Latest test reports:

Max5 - ok
Max6 - ok

MacOS 10.6 & 10.7 (intel32 & 64bit) - ok
MacOS 10.6 PPC - ok 

Windows7 (32bit and 64bit) - ok
------------------------------------
version: maxsdr5c (Mac OS & Windows)
------------------------------------
This project is available in several forms:

1) all files including documentation & tutorials
2) max/msp collective (Mac OS) - 
3) max/msp collective (Windows) - 
4) standalone app (Mac OS) - 
5) git repository - same as 1

I strongly recommend option 1) or 5). You'll greatly increase your chances for success. 

These instructions apply to all versions:

1) unzip the the downloaded file. It will be a folder. You can rename the folder to anything
that's convenient. For example, maxradio or maxsdr5. In this document we'll call it the 
maxsdr5 folder.
2) Add the folder to the Max/MSP user filepath. From the Options : File Preferences menu,
by clicking the '+' in the lower left corner of the File Preferences window, and clicking
the 'choose' button to browse to the folder.

3) Check online documentation for help on how to use the program http://zerokidz/radio

4) FUNCube needs to be plugged in before launching Max

5) Sample rate should be set to 96k or higher for best audio quality and bandwidth

6) The name of the file to run is:

maxsdr5c.maxpat (for full version)
maxsdr5c.mxf (for collective)
maxsdr5c (for app)

If you can't find that file name look for a newer version with a higher letter of
 the alphabet, for example, maxsdr5d.

7) If you hear periodic buzzing (comb filtering) when using the FUNcube, increase the 
signal vector size in Options : DSP Settings (Audio Settings).  Try values of 512, 1024, or 2048 until
the problem goes away or gets less annoying. This is either a problem with the Funcube 
or the FM detector. 
------------------------------------------------------------------
Tutorial patches and documentation are in the tutorial folder. If you move them
somewhere else, you'll still need to have the maxsdr5 folder (described above) in
your max user filepath - because the maxsdr5 folder contains patches and externals
required by the tutorials.
-------------------------------------------------------------------
known issues:
-------------------------------------------------------------------
-Loud buzzing occurs sometimes the first time you toggle audio on - This has happened
on the macbook pro.  If it does happen, it may swamp the AGC and filters - leaving
you wondering why nothing works.  just close the patch and reload it.

- Problems running FUNCube and Soft66lc2 at the same time. Switching back
and forth from within Max seems to cause problems. Workaround: Run the 
devices separately.

- If tuning on either device just stops working. Or you get error messages in 
the Max window whenever you change frequency - try reloading the patch
or restarting Max.

- left/right arrow keys (to change frequency) don't work. This happens when
you click on an object, like a gain slider, that takes control of the 
arrow keys for its own personal use. Workaround: click anywhere in the 
whitespace of the patch. Then try the arrow keys again. We're working on
an alternative…  

- Please read the user manual - maxsdr5b.pdf. You can access online or from the doc/
folder.

-soft66lc2 libraries missing: (see below for solution). 
--------------------------------------------------------------------

Here are the instructions for installing Soft66lc2 library files. If the
Soft66lc2 isn't working please read this first.
----------------------------------------------
Soft66lc2 library files for max radio project:
----------------------------------------------
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
	Referenced from: /Users/tkzic/maxsdr5/sfctrl.mxo/Contents/MacOS/sfctrl	Reason: image not found

Then you've come to the right place. 

First - If your computer has the PPC (PowerPC) chipset there is now hope! The maxsdr5/ppc/ folder
has libraries, a special max external object - with instructions in maxsdr5/ppc/READMEppc.txt,
Read the instructions and then come back here using the PPC versions of the library 
files instead of the ones in the maxsdr5/lib/ folder…

 
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
the lib/ folder to either one of two places:

	c:\ProgramFiles\Cycling'74\Max5.0\   (for Max5)
	c:\ProgramFiles\Cycling'74\Max6.0\ 	(for Max6)

Alternatively You could copy it to the Windows\system32 or 
Windows\system64 directory.

The system may give you warnings about privileges - please ignore them and forge on through.
-----------------------------------------------------
Problems? Questions? Ideas? Interested in developing?  Send email to radio@zerokidz.com

Tom Zicarelli, KA1IS

-----------------------------------------------------
This project was derived from the works of the following developers.

Kazunori Miura, JA7TDO - hardware and software design of soft66lc2
Thomas Horsten - Linux soft66add control software
Thomas Robin-Couerrier - ppc Max external software and library conversion & testing
Howard Long, G6LVB - hardware and software design of FUNCube
Alexandru Csete, OZ9AEC - QTHid FUNCube control software
Mario Lorenz, DL5MLO - FUNCube control software
David Pello, EA1IDZ - Linux FUNCube command line control software.
Joseph Zicarelli, KB1URI - design, technical advice, and testing.

Thank you!





 