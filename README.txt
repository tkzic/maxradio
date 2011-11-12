README.txt for max radio project
November 11, 2011
------------------------------------
version: maxsdr5c
------------------------------------
This program is available in 3 forms:

1) all files - maxsdr5 folder (this is the only way to run in Windows)
2) max/msp collective (Mac OS) - maxsdr5_collective folder
3) standalone app (Mac OS) - maxsdr5_app folder

I strongly recommend option 1). You'll greatly increase your chances for success. 

These instructions apply to all versions:

1) unzip the the downloaded file. It will be a folder.
2) Add the folder to the Max/MSP user filepath in options : file preferences
3) Check online documentation for help on how to use the program http://zerokidz/radio

4) If you hear periodic buzzing (comb filtering) when using the FUNcube, increase the signal vector size in Options : DSP Settings.  Try values of 512, 1024, or 2048 until the problem goes away or gets less annoying. This is either a problem with the Funcube or the FM detector. 

5) Sample rate should be set to 96k for best quality and bandwidth

6) The name of the file to run is:

maxsdr5c.maxpat (for full version)
maxsdr5c.mxf (for collective)
maxsdr5c (for app)

If you can't find that file name look for a newer version, for example, maxsdr5d.

Tutorial patches and documentation are in the tutorial folder. If you move them somewhere else, you'll still need to have the main folder (described above) in your max user filepath - because the main folder contains patches and externals required by the tutorials.
-----

Here are the instructions for installing Soft66lc2 library files. If the Soft66lc2 isn't working please read this first.
----------------------------------------------
Soft66lc2 library files for max radio project:
----------------------------------------------

Several dynamic library files are required for the Soft66lc2 device control external object to load properly in Max/MSP.  If the Max radio patch loads and runs without errors then your computer already has the necessary library files installed. You can safely ignore these instructions.

On the other hand‚Ä¶ if you load the max radio patch and see error messages in the Max window something like:

	sfctrl: unable to load object bundle executable
 	2011-11-11 15:51:06.328 MaxMSP[25680:507] Error loading /Users/tkzic/maxsdr5/sfctrl.mxo/Contents/MacOS/sfctrl:
	dlopen(/Users/tkzic/maxsdr5/sfctrl.mxo/Contents/MacOS/sfctrl, 262):
	Library not loaded: /usr/local/lib/libftdi.1.dylib
	Referenced from: /Users/tkzic/maxsdr5/sfctrl.mxo/Contents/MacOS/sfctrl	Reason: image not found

Then you've come to the right place. 

First - If your computer has the PPC (PowerPC) chipset - We don't currently have libraries available. We're working on this. Sorry. If your computer is Intel 32 or 64 bit, then you'll need to install libftdi on your computer. Libftdi is a library of USB drivers required by the Max external. There are two ways to get it. 

1) (the hard way) Install libraries by downloading and compiling source. Use instructions in this link:

	http://geckodownloads.googlecode.com/files/libftdimacosx.pdf


2) (the easy way) Just copy the library files from the maxsdr5/lib folder to the correct location on your computer using the instructions below.

----------------------------------------------------------
Instructions for copying libftdi library files:
-----------------------------------------------------------

Short version: Copy all of the .dylib files in the maxsdr5/lib directory to: /usr/local/lib

Detailed version:

You'll be typing commands into the terminal console. Terminal is in the Applications/Utilities folder. You'll need your admin password for some of the commands. Just enter it when prompted.

1. See if /usr/local/lib exists. Type:

	ls -l /usr/local/lib

If the response is: "No such file or directory" then create it by typing:  

	sudo mkdir /usr/local/lib

2. To copy the files, first go the maxsdr5/lib folder. (assuming its under your home user folder - otherwise substitute correct folder location for "maxsdr5/lib")

	cd maxsdr5/lib

3. Then copy all the library files:

	sudo cp *.dylib /usr/local/lib

4. Now quit terminal. Return to Max/MSP and reload maxsdr5c.maxpat   

If this doesn't work - please send email to radio@zerokidz.com

-------------

Note: These library files are universal (fat) binaries for intel 32 bit and 64 bit architectures.  PPC versions are coming soon.

-----------------------------------------------------
Problems? Questions? Interested in development?  Send email to radio@zerokidz.com

tom zicarelli


 