Mozzi
=====
sound synthesis library for Arduino
------------------------------------

Version 0.01.2c
Tim Barrass 2010-13


Currently your Arduino can only beep like a microwave oven. Mozzi brings
your Arduino to life by allowing it to produce much more complex and interesting
growls, sweeps and chorusing atmospherics. These sounds can be quickly and easily
constructed from familiar synthesis units like oscillators, delays, filters and
envelopes.

You can use Mozzi to generate algorithmic music for an installation or
performance, or make interactive sonifications of sensors, on a small, modular
and super cheap Arduino, without the need for additional shields, message
passing or external synths.


### Features

-    16384 Hz sample rate, with 8 bit or 14 bit audio output modes.
-    Variable control rate from 64 Hz upwards.
-    Useful basic audio toolkit: oscillators, samples, lines, envelopes, scheduling, filtering.
-    Fast ADC and other cpu-efficient code utilities to help keep audio running smoothly.
-    Example sketches for easy modification.
-    Readymade wavetables and a script to convert your own soundfiles for Mozzi.  
-	 Mozzi is designed to be easy to use, open source and extendable.


### Installation

Download Mozzi from the top of this page and unzip it. It will probably have a
name like "sensorium-Mozzi-2bee818". Rename the unzipped folder "Mozzi". Then,
following the instructions from the [Arduino libraries guide](http://arduino.cc/en/Guide/Libraries):  

In the Arduino IDE, navigate to __Sketch > Import Library__. At the top of the drop
down list, select the option to __Add Library__. Return to the __Sketch > Import Library__ menu. 
You should now see the library at the bottom of the drop-down
menu. It is ready to be used in your sketch.


### Quick Start

To hear Mozzi, connect a 3.5mm audio jack with the centre wire to the PWM
output on the Digital Pin for your board according to the table below. 
Use this as a line out which you can plug into your computer and listen
to with a sound program like Audacity. Try some examples from the
File > Examples > Mozzi menu.

Below is a list of the Digital Pins used by Mozzi for STANDARD mode PWM audio out on different boards.
Those which have been tested and reported to work have an x.
Feedback about others is welcome.

x	 9	Arduino Uno  
x	 9	Arduino Duemilanove  
x	 9	Arduino Nano  
x	 9	Arduino Pro Mini  
x	 9	Arduino Leonardo
x	11	Arduino Mega  
x	11  Freetronics EtherMega  
x	 9  Ardweeny  
x	 9  Boarduino
..14	Teensy  
x	B5  Teensy2  
x	B5(25) Teensy2++  
..13	Sanguino  

For details about HIFI mode, read the [Mozzi core module documentation](http://sensorium.github.com/Mozzi/doc/html/group__core.html#gae99eb43cb29bb03d862ae829999916c4).


### Using Mozzi

Here's a template for an empty Mozzi sketch:

`
#include <MozziGuts.h>   // at the top of your sketch

void setup() {
	startMozzi();
}

void updateControl(){
	// your control code
}

int updateAudio(){
	// your audio code which returns an int between -244 and 243
}

void loop() {
	audioHook();
}
`


### Documentation

There's documentation in the doc folder in the Mozzi download and [online](http://sensorium.github.com/Mozzi/doc/html/index.html).  
There are [hints and tips](https://github.com/sensorium/Mozzi/wiki/Hints-and-Tips-%28*-this-has-content%29) and more help on the Mozzi [wiki](https://github.com/sensorium/Mozzi/wiki/_pages).  
Start or look up a topic on the Mozzi [users forum](https://groups.google.com/forum/#!forum/mozzi-users/).  
Also, feel free to submit any issues on the [GitHub Mozzi site](https://github.com/sensorium/Mozzi/issues/).  
Check for code and usage changes in NEWS.txt.
Also, there are recordings of the examples inside their sketch folders.


### Caveats

While Mozzi is running, the Arduino time functions millis(), micros(), delay(), and
delayMicroseconds() are disabled. Instead, Mozzi provides mozziMicros() for timing, with 61us resolution (in STANDARD mode), and
EventDelay() for scheduling.  Also, Mozzi can be paused (pauseMozzi()/unpauseMozzi()) if the Arduino timers are required for other things.


###Contributions / Included Dependencies

Mozzi makes use of the following code:

[TimerOne library] (http://www.pjrc.com/teensy/td_libs_TimerOne.html)  
[FrequencyTimer2 library] (http://www.pjrc.com/teensy/td_libs_FrequencyTimer2.html) - now a [fork with support for ATmega32u4 processors](https://github.com/sensorium/FrequencyTimer2)   
[xorshift] (http://www.jstatsoft.org/v08/i14/xorshift.pdf) random number generator, George Marsaglia, (2003)  


Mozzi has also drawn on and been influenced by (among many others):

ead~.c puredata external (creb library) Copyright (c) 2000-2003 by Tom Schouten (GPL2)  
[AF_precision_synthesis](http://adrianfreed.com/content/arduino-sketch-high-frequency-precision-sine-wave-tone-sound-synthesis)
by Adrian Freed, 2009  
[Resonant filter](http://www.musicdsp.org/archive.php?classid=3#259) posted to musicdsp.org by Paul Kellett,
and fixed point version of the filter on [dave's blog of art and programming] (http://www.pawfal.org/dave/blog/2011/09/)  
State Variable filter pseudocode at [musicdsp.org] (http://www.musicdsp.org/showone.php?id=23 and http://www.musicdsp.org/showone.php?id=142)  
Various examples from [Pure Data](http://puredata.info/) by Miller Puckette  
[Practical synthesis tutorials](http://www.obiwannabe.co.uk/) by Andy Farnell  