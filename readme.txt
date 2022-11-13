Cumulus readme.txt v.1.9.4 - PLEASE read all of this file!
--------------------------------------------------------------

Cumulus is 'donationware' - if you're happy with it,
please consider making a donation!

Important: On Vista and Windows 7 (and the corresponding server
operating systems), it is strongly recommended that you install 
Cumulus outside the Program Files hierarchy, e.g. put it in 
C:\Cumulus\. If you choose to ignore this advice, you may have 
trouble locating your data files (and any diagnostic files 
produced by Cumulus) as Windows will redirect them to a hidden 
folder. See the FAQ ("I can't find my data files") for more details.
On some systems, depending on how they are configured, this may cause
Cumulus to fail to run at all. You have been warned!

Be careful with the clock on your PC. Try to keep it correct, and
don't allow it to be adjusted automatically within an hour of the
end of your meteorological day. Note that the default setting in
Windows 7 (and possibly other versions of Windows also) is for the
time to be synchronised at 0100 on a Sunday morning - this is 
likely to cause problems!

There also appears to be a bug in Windows 7 with the date format.
It is recommended that before you run Cumulus, you use the following
circumvention:

1) Open Regional and Language Options
2) Under "Format" pick anything else. (eg: English (United States)).
3) Press "Apply"
4) Under "Format" pick your desired locale (eg: English (United Kingdom)).
5) Press OK.

Recent versions of Cumulus attempt to work around this problem, but
carrying out the procedure anyway is a good idea.

The first time you run Cumulus, you'll see a screen asking
you for a few bits of essential information. You can click 
on the 'help' button on that screen for guidance.

If you are upgrading, note that the installer will overwrite
the supplied web templates (in the 'web' folder). If you have
customised them, take copies before completing the install.

If you use VirtualVP, it is recommended that you edit the 
cumulus.ini file (created after you run Cumulus for the first
time) and in the [Station] section, add a line:

VP2SleepInterval = 1100

If you are using a Davis station and have problems getting
Cumulus to connect to it, you need to make sure your
serial port is set to 19200.

Davis stations calculate Sea Level Pressure from Station Pressure
using a formula based on several parameters such as temperature,
humidity, etc, rather than just using altitude as most other
stations do. CWOP require 'Altimeter Pressure' to be uploaded,
i.e. a value calculated simply using altitude. The station does
not provide this value directly, nor the station pressure, so
Cumulus has to read some extra data once a minute in order to
do the calculation. This can take several seconds, so it means 
that a 'normal' data reading may be missed, so you might miss
a high gust value, for example. If you don't use CWOP, or you
are happy for Cumulus to send Sea-Level pressure to CWOP (the
difference is small unless you are at high altitude) add a line
to the [Station] section of cumulus.ini:

DavisCalcAltPress=0

Make sure you always have your station connected to your PC
before starting Cumulus.

It is strongly recommended that you set the archive interval
in your station and the Cumulus logging interval to the same
value. This is particularly important if you have a Davis station
as otherwise you may activate the 'feature' in the Davis stations
where they send the entire contents of the data logger when Cumulus
asks for the data since it was last running. You will need to use
the Davis Weatherlink software to set the station's logger interval, 
and note that chnaging the station's logger interval also deletes
any existing data in the logger.

Note that Cumulus won't be able to operate correctly if 
you set your station logger interval to more than hour (and an 
hour itself may cause problems). It is recommended that you use an 
interval of around 5 to 15 minutes to get the best use of your data.

If you close Cumulus down each night, you should avoid closing it 
down just before midnight (if you use a midnight end of day), 
i.e. when the station will not make any more logger entries before
midnight. This is likely to cause problems when Cumulus starts up
again in the morning, as it will have no 'new' data to read before
it has to do the rollover. In general, it's a good idea to avoid 
stopping or starting Cumulus close to the start/end of the day.

Don't edit (or even open) any of the data files using Excel! 
Use a plain text editor or CSVed - or better still the 
'Cumulus Toolbox' - see the web site downloads section. 
Excel is quite likely to change the date formats, and/or the
field separators, and they have to be in a specific format - in
particular the year has to be two digits rather than four. If you 
want to carry out analysis of your data files using Excel, do it
on a copy of the data.

Cumulus requires a minimum display size of 1024x768. It will work
on smaller displays, and tries to cope, but the display will be
less than perfect. High DPI settings (greater than 100%) may also
cause problems (some text hidden or 'scrunched up').

Note that Cumulus does not read highs and lows from the station, it
maintains its own. This is for several reasons; Cumulus supports an
0900-0900 meteorological day, it works with a number of differing
station types, and it typically maintains more highs and lows than
you station does. It is not practical for me to write and maintain 
separate code to handle some highs and lows differently, or there
would be no Cumulus at all. What this all means is that you may
see slight differences between the highs and lows reported by
your station and by Cumulus. If high accuracy is important to you,
you should be running Cumulus 24 hours a day anyway; but note that
even if you do, there may still be slight differences in the highs
and lows that your station reports due to clock differences and
differences in calculation methods.

If you are using the supplied web templates to create a web
site, you will need to manually upload a few files and create 
an images directory on your web site. See the help file under
"Creating a web site".

Note, if you are upgrading from a previous version, that some 
of the supplied web files may have changed (the javascript
files, in particular) so you should upload the files from
this release once you have finished the installation.

Cumulus doesn't attempt to download any data from loggers from
prior to the point when you first install it. You can force it
to do so, after you have run it the first time, by editing
the timestamp in the today.ini file. You may need to do a little
editing of your data files after doing this, as you may have
duplicate or out-of-sequence entries. 

Note that this does not work for WMR200 stations:  This station 
deletes logger entries when they are downloaded, and there is no 
mechanism for retrieving logger entries for a particular period;
it just sends all the entries that it has. Any data in the station's 
logger will most likely be downloaded and discarded by the station 
the first time you run Cumulus - be warned! You may be able to 
circumvent this by creating a today.ini file in the data 
folder before you first run Cumulus, with just this in it:

[General]
Date=10/04/2012
Timestamp=10/04/2012 10:00:00

Change the dates and time to match the point from which you want 
Cumulus to start downloading data. If the station has already sent 
the data, this may not work, unfortunately. And I can't guarantee
that you will have any success with this method anyway.

Warning: If your weather station is a La Crosse and it is
connected using a serial/USB adapter, then you will probably
have problems using it with Cumulus, in that you will get
erroneous data from time to time. These weather stations are
known to have problems with some serial/USB adapters. There
doesn't seem to be anything I can do about this. For this 
reason, I am sorry to say that I cannot support the use of
Cumulus in this way. Even if you use a direct serial connection,
I can only offer limited support as I don't actually own a La
Crosse station. In particular, if you get bad data from time to
time, I am afraid there is nothing I can do about this; La Crosse
stations appear to suffer badly from RFI (radio frequency 
interference).

Please read the help file!

There is a wiki with lots of useful information at 
http://wiki.sandaysoft.com/

There is an FAQ at http://wiki.sandaysoft.com/index.php?title=FAQ 

Please note that the Vantage Pro/Pro2/Vue USB support appears not to work.
You should use a virtual COM port with the Davis CP210X driver. If
you've been using Weatherlink with your station with the USB setting,
it will have set the station into "USB express" mode. Before you can 
use it with Cumulus, you need to first run Weatherlink and change to
serial mode via the virtual COM port. See the FAQ for further details.

You cannot normally run Cumulus at the same time as other weather
station software (with the same weather station), unless you are
using something like Virtual VP for a Davis station, or are making
some other provision to specifically allow it. But note that Virtual
VP and the Davis DLL which Cumulus uses to communicate with the station
do not seem to get on with each other, some people experience problems; 
I did myself when I tried to use it. 

Don't allow your PC to hibernate/sleep/suspend while Cumulus is
running - you will lose data! Don't disconnect your station while
Cumulus is running; Cumulus only catches up with logger data when
it starts up, it won't be able to catch up with the data that
it missed while you station was unplugged unless you close Cumulus
before you disconnect your station, and connect your station again
before you start Cumulus up - i.e. your station must be connected
to your PC all the time that Cumulus is running. Unplugging a station
while Cumulus is running can cause high CPU usage in Cumulus, which 
continues even after you plug it back in again.

If you change your system date or time format, or other regional settings
such as the list separator, after you have been running Cumulus for some 
time, this will cause problems, as Cumulus will no longer be able to 
recognise its own data, and Windows will no longer be able to recognise 
and convert the dates and/or times for Cumulus. Similarly, don't edit 
the log files to add your own text or other information.

During the install, you will be offered the choice of installing
the HTML files. If you are upgrading and have modified the supplied
web pages, you might want to untick this option, to avoid them
being overwritten by the installer. The installer will in any case
install the new pages to the 'originals' folder in the 'web'
folder, so you can examine them to see if anything has changed 
that you might want to incorporate in your versions.

Each time Cumulus starts up, it creates a backup of the current
'live' files, so that you can easily 'rewind' to the same point
if you have a problem later. The backed up files go in a subfolder
of the 'backup' folder in the Cumulus installation folder. The name
of the folder is based on the date and time - yyyymmddhhmmss - so
that you can easily find the appropriate one. It keeps the latest
ten backups. You perform the rewind by stopping Cumulus and copying
all of the files from the appropriate backup folder to the data 
folder. If you rewind to the previous month, you also need to 
delete the log file for the current month, or you will get duplicate
entries in that file. 

Note that you cannot rewind if you have an Oregon Scientific station.

From version 1.9.3, Cumulus also creates a 'backup' set after each
daily 'roll over'.

Do not create your own files or folders in the backup
folder, as this will interfere with the backup mechanism. Indeed,
you should not store your own files anywhere within the Cumulus
installation folder or its subfolders!

Cumulus assumes a certain level of weather station functionality.
It checks that it has received data from a number of sensors
(e.g. pressure and outside temperature) before it starts logging 
or uploading to the web. You can override this - see the FAQ.

If you need to edit cumulus.ini for any reason, always do this with
Cumulus stopped.

-------------------------------------------------------------

Upgrading:

If you are upgrading from a previous version, you can install 
this version over the top of these (just run the setup.exe).
Your data files will be saved (you should take backups 
before upgrading to be safe). 

An upgrade doesn't change or lose any data or settings. You should 
of course check everything after the upgrade to make sure all is
still as it was.

Uninstalling:

Only the files which were created by the installer are removed.

------------------------------------------------------------

I hope you find Cumulus useful. I am happy to receive bug
reports, comments, and requests for new features, but please
don't email me or use the contact form. I can't do 'personal'
support. Please use the forum at http://sandaysoft.com/forum

You might even want to make a small donation? 
See the 'Help : About' box in Cumulus. But please make sure that
you have tried Cumulus for a while and you're happy with it,
before donating.

This product includes software developed by the OpenSSL Project
for use in the OpenSSL Toolkit. (http://www.openssl.org/) 
Copyright (c) 1998-2008 The OpenSSL Project.  All rights reserved.

Steve Loft
October 2013
