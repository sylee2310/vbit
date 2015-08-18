# Introduction #

MiniTED is a teletext editor. MiniTED used to be an editor sold by MRG Systems. This MiniTED has the same name but is a new development and is designed to run on 32 bit Windows systems.

# Capabilities #

It can be used to read, edit and write teletext pages, but not yet carousels. It handles language flags and other attributes. Pages are compatible with MRG inserters and VBIT.


# Distribution #

MiniTED is still under development but if you would like to try MiniTED then please go to https://www.dropbox.com/sh/6bb3n19d2vi28cz/AADC_JfuphLcc0r1cfiz9IIja.

# Bugs #
Documents have pointers which are not handled correctly and so closed documents pop up again but empty. Ignore these phantom pages.


# Installation #
  * Download the zip file and unzip it in a temporary folder.
  * Click on setup.exe
  * Change the Project1 folder to something more meaningful like Minited. MiniTED is normally installed in c:\minited but c:\Program Files\minited will do.
  * When it finally gets to copying it will probably say "A file being copied is older than the file currently on your system". When it says "Keep this file" always say "Yes".
  * Before you run Minited make this directory structure:
```
 c:\minited\Inserter
 c:\minited\Inserter\OnAir
 c:\minited\Inserter\Pages
 c:\minited\Inserter\User
 c:\minited\Inserter\Log
 c:\minited\Inserter\Readback
 c:\minited\Inserter\Schedule
 c:\minited\Inserter\Schedule\Archive
```
  * If the fonts come out all WingDings then they aren't installed correctly. Find the font files (**.FON) and right click on each one, and select Install.
  * Now you have everything installed you can go back to the downloads section and grab OnAir.zip. Unzip this into the OnAir directory then you will have some pages that you can see how they are made.**

The manual is coming later but just to get you started:
  * Make a new page.
  * Put a graphics/white symbol in the first column on all the rows. For each row click on the character position and then the graphics white symbol (three white dots). These appear as Gw characters.
  * Use the mouse to draw to the right of the Gw characters. It will trace out the path of the mouse in graphics.
  * To do editing at the pixel level use the arrow keys to move to the pixel that you want. You can then use the space bar to flip the pixel between foreground and background colour.
Any bug reports or feature requests to peterk **underscore** vt80 **at** gmail **dot** com