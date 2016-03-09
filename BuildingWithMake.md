# Building ArduPilotMega with Make #

## Overview ##
The APM source code includes a make-based build system that closely emulates the Arduino build process.  This allows developers to integrate the APM build process into other development environments.

This build system also allows multiple projects to be built simultaneously, making it easier to perform check builds of all of the dependent projects prior to a check-in.

## Requirements ##
Currently the APM makefiles work on Mac OS and Linux.  Arduino-0022 or later is necessary.

### Mac OS ###
Mac OS system requirements are straightforward:

  * A working, current Arduino install.
  * Apple Developer Tools (a free download from [Apple](http://developer.apple.com)).

Arduino should be installed in a location that is indexed by Spotlight.

### Linux ###
Linux system requirements vary depending on the distribution.  The following are essential:

  * A working, current Arduino install.
  * The GNU make utility, often referred to as 'gmake'.
  * The GNU awk utility, often referred to as 'gawk'.  You can test for the presence of this tool with the 'which gawk' command.

Use your system's software installation tools as necessary to ensure these components are installed.  Configure Arduino and test building a simple sketch to ensure that your Arduino environment is functional.

### Windows ###
Whilst the build system is not yet functional on Windows, this section outlines the basic requirements:

  * A working, current Arduino install.
  * A basic Cygwin installation, with the GNU make and GNU awk packages also installed.

Currently missing from the Windows environment:

  * A way to locate Arduino on the system without manual intervention.
  * A way to call the WinAVR compiler from gmake without making the makefile nonportable or unmaintainable.

## Preparing ##
The build system expects that the sketch it is building is located inside the sketchbook.  The easiest way to achieve this with APM is to use the convenience sketchbooks provided.

Check out the trunk sketchbook from `https://ardupilot-mega.googlecode.com/svn/Sketchbook/trunk`.

Note that none of the Arduino IDE settings are consulted by the build system.  The sketchbook location is determined exclusively from the sketch location, and the board type is specified by the Makefile in each sketch.

## Building ##
To build a single sketch, invoke `make` with no arguments in a sketch directory:
```
$ cd work/Sketchbook/ArduPilotMega
$ make
%% param_table.o
%% ArduPilotMega.cpp
%% ArduPilotMega.o
...
%% ArduPilotMega.elf
%% ArduPilotMega.eep
%% ArduPilotMega.hex
```
The output of the build is, by default, located in $TMPDIR/_sketchname_.build

To build all of the sketches in the sketchbook, invoke `make` with no arguments in the sketchbook directory:
```
$ cd work/Sketchbook
$ make

%%%% Making all in ArduCopterMega/ %%%%

...


%%%% Making all in ArduPilotMega/ %%%%

...
```

For each sketch, successful completion can be assumed if no errors are reported.

## Uploading ##
Uploading is not currently implemented.  The adventurous can take the .hex and .eep files and program their APM manually using the avrdude commandline that Arduino prints when the upload button is clicked while the Shift key is held down.

## Build Options ##
The build process supports a number of options that can be specified for both single-sketch and sketchbook-wide builds.  Most options are specified in the format _NAME_=_value_ on the make commandline, or in the environment.
<dl>
<blockquote><dt>VERBOSE=1</dt>
<blockquote><dd>Normally the commands being executed to perform the build are suppressed, and only progress information is printed.  Setting VERBOSE to any value will cause these commands to be printed as they are executed.</dd>
</blockquote><dt>SKETCHBOOK=<i>path</i></dt>
<blockquote><dd>Overrides the default sketchbook location and specifies an alternate location for the sketchbook.  The build system looks lfor libraries and hardware support in the sketchbook.</dd>
</blockquote><dt>BUILDROOT=<i>path</i></dt>
<blockquote><dd>Specifies the directory in which intermediate files are placed during the build.  Defaults to $TMPDIR/<i>sketchname</i>.build</dd>
</blockquote><dt>ARDUINO=<i>path</i></dt>
<blockquote><dd>Overrides the automatic detection of the Arduino install location and forces the build system to consider this path the root of the Arduino installation.  For Mac OS users, this is the Arduino.app/Contents/Resources/Java folder.</dd>
</blockquote><dt>TOOLPATH=<i>path</i></dt>
<blockquote><dd>Overrides the automatic detection of the compiler tools path.  For Linux systems, tools are expected to be in a directory named in $PATH.  For Mac OS, tools are normally located inside the Arduino application.  To use the AVR CrossPack compiler on Mac OS, set this to /usr/local/CrossPack-AVR/bin.</dd>
</blockquote><dt>AWK=<i>path</i></dt>
<blockquote><dd>For Linux systems where GNU awk is not installed as 'gawk', set this to the name of GNU awk.</dd>
</blockquote><dt>-j <i>number</i></dt>
<blockquote><dd>Build speed may be increased by specifying <i>number</i> greater than 1.  Note that error messages from multiple source files may be intermixed if this option is used.</dd>
</dl></blockquote></blockquote>

## Troubleshooting ##
The build process itself attempts to diagnose problems that would prevent a successful build outside of code errors.  It may emit the following diagnostics:

<dl>
<blockquote><dt><code>WARNING: More than one copy of Arduino was found, using ...</code> (Mac OS only)</dt>
<blockquote><dd>Spotlight found more than one copy of Arduino installed on your system.  Check the path that is printed to ensure that the correct version is being used.  To avoid this problem, either remove old versions of Arduino or specify the ARDUINO option when invoking the build system.  Typically the installation that will be chosen is the one that was most recently launched.</dd>
</blockquote><dt><code>ERROR: must set BOARD before including this file.</code></dt>
<blockquote><dd>The sketch Makefile has not defined the BOARD variable.  This is normally set to <code>atmega1280</code> for APM.</dd>
</blockquote><dt><code>ERROR: Spotlight cannot find Arduino on your system.</code> (Mac OS only)</dt>
<blockquote><dd>Arduino is not installed, or it is installed in a location that is not being indexed by Spotlight.  You can either enable Spotlight for the location where Arduino is installed, or specify the location explicitly by setting the ARDUINO option as described above.  Note that Spotlight indexing may take some time, so enabling it for the location containing Arduino may not immediately correct this issue.</dd>
</blockquote><dt><code>ERROR: Cannot find Arduino on this system, please specify on the commandline with ARDUINO=&lt;path&gt;</code> (Linux and Windows only)</dt>
<blockquote><dd>Arduino was not found in one of the standard locations (/usr/share/arduino, /usr/local/arduino) and there is no efficient system-wide search facility to find it.  Either move Arduino to a standard location, or specify its current location with the ARDUINO option.</dd>
</blockquote><dt><code>ERROR: cannot find the compiler tools anywhere on the path ...</code></dt>
<blockquote><dd><p>The compiler and related tools cannot be found.  For Mac OS and Windows the tools are normally part of Arduino and this message indicates that the Arduino installation is damaged.</p><p>For Linux systems, this means that the AVR tools are not installed in a standard location.  Either set the TOOLPATH option to point to the directory containing the AVR tools, or install them in a standard location.  Normally installing Arduino on a Linux system will result in a correct installation of the AVR tools.</p></dd>
</blockquote><dt><code>ERROR: sketch SketchName is missing SketchName.pde</code></dt>
<blockquote><dd>Arduino requires that a sketch directory called SketchName contains a file called SketchName.pde.  This file was not found.  Either the directory containing the Makefile is not a sketch directory, or there is a problem with sketch naming.  On Windows systems, check that the capitalisation of the sketch directory and sketch file names matches exactly.</dd>
</blockquote><dt><code>ERROR: cannot find gawk - you may need to install GNU awk</code> (Linux and Windows only)</dt>
<blockquote><dd>The GNU awk utility is required, but it has not been installed or cannot be found.  Check that <code>gawk --version</code> works at the command promp.  You may need to specify its location explicitly with the AWK option.</dd>
</blockquote><dt><code>ERROR: hardware directory for ... not found</code></dt>
<blockquote><dd>The optional HARDWARE setting in the sketch makefile specifies hardware that is not supported by the chosen Arduino installation, and not supported by any alternate hardware directory in the sketchbook.  Either correct the HARDWARE setting or install the required support.  If the named hardware is <code>arduino</code> then the Arduino installation is damaged.</dd>
</blockquote><dt><code>ERROR: could not locate boards.txt for hardware ...</code></dt>
<blockquote><dd>The boards.txt file is missing from the hardware support directory for the named hardware. If the named hardware is <code>arduino</code> then the Arduino installation is damaged.</dd>
</blockquote><dt><code>ERROR: could not locate board ... in ...</code></dt>
<blockquote><dd>The BOARD setting in the sketch Makefile is not compatible with the HARDWARE setting.  If there is no HARDWARE setting in the board file it defaults to <code>arduino</code>, and in that case the BOARD setting refers to a board that is not supported by the chosen Arduino installation.</dd>
</dl>