## Using Tortoise SVN ##

The APM developers use a version control system and code repository called Subversion, which is hosted on Google Code.  Code changes are "committed" in to the repository, and you can "Check out" code, and "Update" to the latest version, along with many other more advanced code management options.

If you're going to use and contribute code to the development branch, you'll need to do it within Subversion. (Public code is distributed via a zip file, but contributors must work within a version control system)

The simplest way to use Subversion (SVN) if you're using Windows is to use a SVN client called TortoiseSVN. Here's how:

1) Download Tortoise [here](http://tortoisesvn.net/downloads.html), selecting either 32 bit or 64 bit depending on which version of Windows you're using. Install it. You won't see anything you can run--that's because it integrates itself into the Windows right-click folder and file menus, as shown here:

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/tortoise.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/tortoise.png)

2) To get the code for the first time, right click anywhere on your desktop and select "SVN Checkout". This will take you to a dialog box that will allow you to select two important things: A) the URL of the folder in the online SVN repository you want to download and B) the folder on your computer where you want to put it.

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/tortoise3.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/tortoise3.png)

Click on the the little "..." box to the right of each of those to bring up the option to select the right one. First, start with the repository URL...

3) When you click on the repository "..." box you'll be taken to the Repository Browser. Use that to navigate to the right URL. In most cases, we will have established a special "Sketchbook" folder for the main code branches. That Sketchbook will collect the code from all the various necessary folders and put it in one folder on your desktop. Here, I've select the "trunk" of the ArduPilotMega, which is the main development code.

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/tortoise2.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/tortoise2.png)

4) Now pick or create a folder on your desktop to put the code in and press OK. Tortoise should open a window and show you all the files being downloaded

5) Once you've downloaded a Sketchbook, you must tell Arduino that you'll be using that. Go into the Arduino Configuration menu and enter the folder you loaded the code into. When you're done, you must close Arduino and open it again:

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/tortoise4.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/tortoise4.png)

You should now be able to run the code in that folder and Arduino will find any libraries there.

6) Once you've Checked Out a folder, you can updated it to the latest code by right-clicking on the folder and selecting SVN Update.

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/tortoise5.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/tortoise5.png)

7) If you are going to make changes to code and want others to see and be able to use them, you must "Commit" them back into the repository. Tortoise will ask you for your username and password. Your username is just your email address that you use for your Google account. Your password may be found by click on "google.com password on [this screen](http://code.google.com/p/ardupilot-mega/source/checkout), as shown here:

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/tortoise6.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/tortoise6.png)