# Introduction #

TED Scheduler was a product of http://www.mrgsystems.co.uk. It was used to control various types of teletext inserter in conjunction with MiniTED. TED Scheduler can control most of MRG's inserters. It can also control Astet devices like Atom, Quark and TDG7. It has now been updated to control VBIT. TED Scheduler is not yet freely distributable. If you would like to try TED Scheduler then please contact me, Peter Kwan.

# Scheduling #

TED Scheduler operates by creating schedules. Schedules sometimes operate immediately or they can be timed. Schedules can also repeat. Schedules are simple text files that contain a schedule time and a list of commands. TED Scheduler comes with two schedules already installed and these are used for deleting old log entries. Other schedules can be added to set the time and date and this is very useful for VBIT which has no battery backed up real time clock.

For each inserter there is a Schedule folder. For single inserter systems this is usually in c:\minited\inserter\schedule. As soon as a schedule is written to this folder and the schedule execution time is reached, the schedule will be executed. Once executed it will be moved to the Archive sub folder. If the schedule is marked as a repeating schedule then the schedule will be rescheduled accordingly.

MiniTED, the teletext editor is designed to write TED Schedules. When the Send button is clicked a schedule is written out for immediate transmission. The schedule contains a command to send the page.

Schedules can be created by any method that is convenient including Notepad. For example, the weather could be read in by XML, and transformed to a schedule file by XSL.

# File Structure #
The root of the system is expected to be c:\minited\. TED Scheduler is in a sub folder at c:\minited\inserter. The executable is Scheduler.exe. The supported inserter types are defined in InsTypes.ini. The initialisation are in inserter.ini. The sub folders are
  * Log - Log of scheduler activity
  * OnAir - Pages that are currently on air
  * Pages - A library of Pages
  * Readback - Pages that have been read back from an inserter (used mainly for inserters that can capture pages)
  * Schedule - Schedule files to control the inserter. There is also an Archive sub folder where the schedule files go after being executed.
  * User - Similar to Pages. Not really sure how old MiniTED handles users.

# TED Scheduler and VBIT #
VBIT is partially supported. It is possible to upload new pages. It can also set the header time and details. For a new system we will assume that you are using the standard setup of MiniTED in c:\minited\. The TED Scheduler executable should be placed at
c:\minited\inserter\Scheduler.exe. It also requires the Scheduler.ini and InsTypes.ini files or it will get terribly confused. To configure the system you should run this and then set up communications as follows:
## VBIT Comm Port ##
This assumes that you have plugged in VBIT and installed the serial port driver INF file. To find the VBIT Comm port you can try using TED Scheduler. Under the tabs Setup->Connection make sure that Com Port is selected. Then press the Comms Setup... button. Your COM port will probably be the highest number port in the list. Select Direct to COM4 or whatever it is. As a virtual com port the baud rate is irrelevant so ignore this.

Now click the button marked Detect Inserter... It should now say VBIT620. If it doesn't connect then look at the information panel. It will probably be telling you about timeouts. Just keep trying. The system doesn't always connect the first time. Once you get connected make sure that Setup->Connection is saying "Inserter: VBIT620" and the Protocol selected is VBIT USB.

You will notice that your inserter time always starts at 10:00.00. This is because there is no battery backed clock. Press the Set Time button and OK the dialogue box. The time will update within a few seconds and now be correct. However, the date will still be wrong! Go to Setup->System and edit the header. You can add some date fields to the header.
> Example: mpp Goto80 DAY MTH dd

To actually send the header, right click in the "Header" box and select "Write header" from the pop-up menu.

When you send the header it isn't updated immediately but only when the page is retransmitted so it could be a minute until the header updates.
Also, the header needs to be updated with the new date every day. Ideally you would automate this with a schedule.

## To Make a Date/Time updater schedule ##
Go to Schedules and click the white document sheet (tool tip is New Schedule). Give it a file name and a description. In the textbox marked command put the time command in "T". Select the Repeat to happen every day.
https://picasaweb.google.com/lh/photo/LrZMJakeSbCM5kBXjgKDGLl2kz7rIuTkxf4CMOW-s2M?feat=directlink
This only sets the time. You also need to set the date. This is done in the header.

Click on the Schedules tab and select Sync.sct. This calls up the schedule editor. Add the OH (output header) line and if you want to run the schedule immediately, then set the AT date to a time in the past.
```
AT,25/09/12,00:00
DE,Setting system time:
OT
OH mpp Goto80 DAY MTH dd
RP,1,00:00 
```
Then click on the Save to disk icon, and save Sync.sct back into the Schedules folder. The schedule will operate immediately, and then will repeat once a day.
## VBIT not connecting? ##
### Installing the correct driver ###
The correct driver is installed by using the MT-X1.INF file. More details to be added here.
### Checking the Com number ###
How to verify that you have the correct port number. In Setup go to the Hardware devices manager. In Windows 7 this is Control Panel->System and Security->System then click on Device Manager. Click on Ports (COM and LPT). On my system it says **MT-X1 CDC (COM4)**. This means that it is the MT-X1 CDC driver which is the correct hardware, and that it has been allocated COM4.
### VBIT Still not connecting? ###
Try restarting VBIT. This will force anything using the COM port to disconnect. Restart VBIT then restart Scheduler.exe. Try typing Y

&lt;enter&gt;

 in the Expert Window. It should respond with the version number.
### VBIT not an option? ###
The Header update menu simply isn't there when you select VBIT. Also VBIT does not appear in the "Choose Inserter" list. This is because you have an old version of InsTypes.ini. The latest InsTypes.ini implements VBIT and you should replace the old copy and restart Scheduler.


# Details #

For more details you'll need to check the TED Scheduler manual.