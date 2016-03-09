# Submitting Code Patches #

Below are instructions for the best way to submit patches to the ArduCopter or ArduPlane code base.


## Create a public clone in the arduPilot-mega git repository ##

To create, test and eventually submit a patch to be included in trunk, you first need to create a publicly visible copy of the ardupilot-mega code base in a public clone.  In order to make changes to this public clone you must also make a local clone as shown below.

![http://wiki.ardupilot-mega.googlecode.com/git/images/GitInstructions/GitCreateClone.png](http://wiki.ardupilot-mega.googlecode.com/git/images/GitInstructions/GitCreateClone.png)

1. go to the [ardupilot-mega](http://code.google.com/p/ardupilot-mega/) web page and select **Source**, **Clones** or just click [here](http://code.google.com/p/ardupilot-mega/source/clones)

2. click on the clones button at the bottom

![http://wiki.ardupilot-mega.googlecode.com/git/images/GitInstructions/CreatePublicClone.png](http://wiki.ardupilot-mega.googlecode.com/git/images/GitInstructions/CreatePublicClone.png)

3. fill in the name, summary, description and press the "Create repository clone" button

4. find your new clone in the [clones web page](http://code.google.com/p/ardupilot-mega/source/clones), click on it and copy the command to create the clone on your local PC (you will run this in a moment)

![http://wiki.ardupilot-mega.googlecode.com/git/images/GitInstructions/CreatePublicClone3.png](http://wiki.ardupilot-mega.googlecode.com/git/images/GitInstructions/CreatePublicClone3.png)

5. Create a local clone (on your harddrive) of your public clone.  The steps are the same as Step #3 on [this page](http://code.google.com/p/ardupilot-mega/wiki/Git) with the exception that you should use the URL captured in step 4 above.

## Test your changes thoroughly ##

## Submit the patch for code review and inclusion into trunk ##