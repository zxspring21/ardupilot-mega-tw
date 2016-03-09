# Introduction #

This tutorial demontrates how to setup an external editor, specifically AVR studio, to develop one's software; and guides the user through the process of loading the software to the APM via the AVRdude application.

# Details #

## Download/Install Necessary Software ##

1. First download **Avr** **Studio** (the official IDE from Atmel - AVR Studio 4.18 (build 684) (116 MB, updated 11/09)) and its latest service pack, currently **SP3**.

http://www.atmel.com/dyn/products/tools_card.asp?tool_id=2725

2. Download the **Winavr** **IDE** containing the C compiler that will be integrated into the Avr Studio.

http://sourceforge.net/projects/winavr/files/WinAVR/20100110/WinAVR-20100110-install.exe/download

3. Install all downloads.

## Prepare PC for Future AVR Projects ##

4. Create a folder in your root directory for all AVR studio projects to make it easy for the compiler to find your project files **(C:\AVR)**

## Setup AVR Studio and Create a Project ##

5. Boot up AVR studio

6. Open a new project and call it **Blinky**.

7. Select the project type and check boxes “Create initial file” and “Create folder.”

8. Click next to advance to the screen shown below.

9. For the Atmega2560, select the **“AVR Simulator”** as the debug platform.

10. Select the appropriate chip and click finish (ATmega2560)

11. Copy and paste the code below into the .c file that was created for you.

```
#include <avr/io.h>
#include <util/delay.h>

#define F_CPU 16000000UL

int main(void)
{    
DDRC |= (1<<PC0);
	while(1)
	{      
		PORTC |= (1 << PC0);
		_delay_ms(10000);      				
		PORTC &= ~(1 << PC0);
		_delay_ms(10000);
	}
	return 1;
}
```

12. Press F7 to compile the software and make sure that it compiled without error.

## Prepare for the Compile ##
13. Open notepad and copy the text seen below. Save it as a .txt file for now. Later you will save this as a .bat file to help ease your compile process. (The first directory path is pointing to your avrdude application file. The second directory path is pointing to the avrdude.conf file, and the third is pointing to the compiled software file for the project that you want to load onto your APM. Make sure that these directories match those on your PC. Once that is done, modify your COM port as needed.)

**C:\WinAVR-20100110\bin\avrdude -CC:\WinAVR-20100110\bin\avrdude.conf -v -v -v -v -patmega2560 -cstk500v2 -P\\.\COM3 -b115200 -D -Uflash:w:C:\AVR\Blinky\default\Blinky.hex:i**

14. Once you are done modifying the command save the text file. Now, save another copy of this file, with a .bat extension, in a location that is easily accessible during software development (desktop).

15. To load your APM with your software first depress the reset button on the oil-pan near your z gyro.

16. Next, double click your .bat file to begin programming your APM. Once WINDOWS opens up a command console window, release the reset button and you should see the command console print a bunch of text as it programs your APM.

## Your Done! ##

17. Enjoy your newly programmed APM.

## It Didn't Work?? ##

18. If the command window output or your APM gives you the indication that your download failed, then try the following steps.

19. Download and install the **Arduino IDE**.

http://www.arduino.cc/en/Main/Software

20. Open the Arduino IDE example Blink. If it doesn’t appear in the IDE example section, find the location where you downloaded the IDE to and find the example/Basics/Blink.c file. The code can be seen below.

```
/*
  Blink
  Turns on an LED on for one second, then off for one second, repeatedly.
 
  This example code is in the public domain.
 */

void setup() {                
  // initialize the digital pin as an output.
  // Pin 13 has an LED connected on most Arduino boards:
  pinMode(13, OUTPUT);     
}

void loop() {
  digitalWrite(13, HIGH);   // set the LED on
  delay(1000);              // wait for a second
  digitalWrite(13, LOW);    // set the LED off
  delay(1000);              // wait for a second
}
```

21. Modify the Blink.c by swapping pin 13 for pin 37. As seen below.

```
/*
  Blink
  Turns on an LED on for one second, then off for one second, repeatedly.
 
  This example code is in the public domain.
 */

void setup() {                
  // initialize the digital pin as an output.
  // Pin 37 has an LED connected on most Arduino boards:
  pinMode(37, OUTPUT);     
}

void loop() {
  digitalWrite(37, HIGH);   // set the LED on
  delay(1000);              // wait for a second
  digitalWrite(37, LOW);    // set the LED off
  delay(1000);              // wait for a second
}
```

22. Hold the Shift key and press the upload button to trigger the Arduino IDE to output verbosely while uploading software to the APM. Upon pressing the upload button, immediately click in the black status window at the bottom of the IDE and be prepared to CTL+A and CTL+C in succession once the terminal begins outputting the download status. Doing this will copy the output including the call to the avrdude application by the Arduino IDE. You can copy and paste this command into your .tx/.bat file from steps 13/14. Retry steps 15 and 16 and enjoy your programmed APM.
