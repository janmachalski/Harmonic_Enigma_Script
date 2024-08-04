# Harmonic Enigma Script for Kontakt
## About
Harmonic Enigma Script v1.0341\
This is my swiss knife script for manipulating tunings, scales and harmonies inside Native Instruments Kontakt.\
I made is as my personal project. Right now I'm to lazy to record a proper tutorial but I might do one in the feature if people are interested.\
Consider supporting me on patreon :) \
patreon.com/ioannivarsovius

## Requirements
Kontakt v. 6.8 (previous versions might also work but there has been some glitches observed in Kontakt 5).
## Setup
Copy the script code and past it inside Kontakt instrument script editor. Once loaded you can save it as a preset to quickly recall the script in other instruments.
### Troubleshooting
Unfortunately Kontakt has 5 script slots and sometimes all of them are taken by default. If this is the case, you might have to delete one of the current scripts or redo the instrument whatsover.
### Known issues
1. The interval of equivalence can be set to any ratio, including values less than or equal to 1.0 which causes errors in the calculations.
1. Link option doesn't work in the AU version of the Kontakt plugin. It is caused by the .AU format itself. Use a vst3 instance of Kontakt, if possible.

## Why another microtuning script?
I wanted to create a tuning script that would allow me to easily automate any microtonal changes procedurally inside my favourite octave and non-octave tuning systems.
### Automation
Most existing scripts are limited in one way or another, mainly in terms of automations. I wanted to be able to automate microtonal tunings freely and change them dynamically. Most of the time user input is done through ui_value KSP objects which do not allow any kind of automation. Midi is limited to 128 note classes. Automation extends the possible number of pitch classes above this limit.
### Script range
I wanted to be able to assign the script range. I also included options to only map white or black keys - it is a helpful feature for microtonal tunings because Halberstadt keyboard layout is not suitable to xenharmonic tunings.
### Transposition
I wanted to be able to freely transpose through different microtonal keys, mainly using common-note transposition.
### Script linking
You can send MIDI outside of Kontakt and route it to another instance to control the tuning of different instruments from one place. Normally, if you want to change a microtonal tuning you have to do it through pain in every instrument. If you use the linking option of this script, you can manipulate scales and tunings everywhere from one place. E.g. you can modulate to a different key just by turning a single knob, and every other connected instance will follow.\
To use this option you have to go to Kontakt Options->Engine and enable script generated notes and CCs in the "send MIDI to outside world" option. Then, in your prefered DAW, route MIDI from a "master" plugin instance of Kontakt to every other instance that you wish to control. You can use your mouse to change parameters and record MIDI that goes from this "master" instance. Any instance can be the "master" one, as long as it is routed to others in the DAW. Note that AU plugins don't support sending MIDI, so you should use vst or vst3 versions of Kontakt.\
Kontakt normally is painful to automate - you have to assign every parameter manually. The goal of this script was to overcome this limitation. Now you can uickly create a complex microtonal setup.
### Correct zone playback
In all of the scripts I've seen, if you tune a note up by 200c it will play the same zone tuned by 200c even if there exist a separate zone a wholetone above, that could be played with 0 transposition. I want the sampler to execute the nearest zone to a given pitch. It's not a problem in single sample instruments, but when I use a deep-sampled instrument I want to use it's full potential.
### Octave reduction
I wanted to implement different octave reduction methods, e.g. "alias" mode where an interval above an octave is reduced not by an octave but by the interval difference from the octave, e.g. major 10 would go to a minor 6th. I also wanted to implement non-octave systems.
### Pedaling
Pedaling switches are included in the script to act as sharp/flat switches that can be finetuned microtonally.
### BPM overtones
I included a mode in which every note (after it has been tuned) is quantized to the overtones of the duration of a bar. E.g. if the tempo is 120bpm and the time signature is 4/4 the duration of a bar is 2s, or 0.5Hz. When enabled, every note frequency is quantized to the multiples of 0.5Hz. It's a subtle difference, but when you play chords, the beating envelope of sounds becomes in sync with the project tempo. This relies on the correct finetuning of the original samples.
### Adaptive Just Intonation
You can momentarly switch on the adaptive just intonation. It's an experimental feature to allow infinite comma pumps. Basically, you can play triads of the Benedetti's puzzles and the script will calculate the correct pitch drift infinitely.
### Zalewski's harmonic structures
I wanted to implement an automatable calculator for scripting Zalewski's harmonic structures live.
### Epimoric system
I wanted to be able to use a tuning system that I created for my composition called "Epimoric Music". \
You can listen to it here: https://www.youtube.com/watch?v=yFuzTY85e2Q
\
The original project was made in Max MSP but I recreated it's features in KSP.\
I will try to explain them briefly using my limited english vocabulary: The important think is that I enjoy the harmonies that this system proposes. There are some nice prime number sequences that I like to explore musically and geometrically. This system involves combining ratios in a form of (n+m)/m or n/(n+m) where n and m are simple integers. Those look pretty mathematically because the increments of m create consecutive steps of the scale, e.g. for n=5 m goes from zero to five forming a pentatonic with frequency ratios: (5+0)/5; (5+1)/5; (5+2)/5; (5+3)/5; (5+4)/5. I call those variables modus and gradus. Then, starting from any of the pitch classes, i construct a conjunct scale in a same manner. In the composition "Epimoric Music" I used only modus=3. The ratios (n+m)/m are similar to the harmonic mean monochord operations. Ratios in a form of n/(n+m) are similar to the arithmetic mean. I understand harmonic and arithmetic means as otonal and utonal harmonies, that is major-like overtone segments and minor-like undertone (subharmonic) scales. The core of this harmonic system are not the scales themselfs, but the fact, that they are transposed and modulated through common-tones. I find all of those possible connections very musical and I often use them as a compositional technique. I later expanded the rules of those tranpositions outside of the "epimoric scales" to all circular tuning systems. This is the gist of it.\
While working on this project I was fascinated by the properties of superparticular (epimoric) ratios. I also used them in place of "standard" prime numbers inside the fundamemtal theorem of arithmetic. I think it's an interesting concept so I will mention it briefly:\
The "epimoric notation" is similar to the Monzo notation (please refer to Tonalsoft encyclopedia) but is based on "(p+1)/p" ratios and not singular "p", e.g. 3=[0,1] in Monzo notation but it's [1,1] in the epimoric one, because 3=2<sup>0</sup>* 3<sup>1</sup>=(2/1)<sup>1</sup>* (3/2)<sup>1</sup>. When writing down natural integers the 'epimoric notation' seems less random than the Monzos (which are simple prime factors), because the total number of factors increases steadly with nearly every integer. I also prefer to think how many octaves (2/1), fifths (3/2) and major thirds (5/4) there are from a given fundamental and not how many 2nd, 3rd and 5th multipliers there are. Below are examples of this notation for numbers 1 to 13:

#### Prime factors (Monzos) of natural integers (integer as a product of p<sup>n</sup>):
1 = [0];\
2 = [1];\
3 = [0, 1];\
4 = [2];\
5 = [0, 0, 1];\
6 = [1, 1];\
7 = [0, 0, 0, 1];\
8 = [3];\
9 = [0, 2];\
10 = [1, 0, 1];\
11 = [0, 0, 0, 0, 1];\
12 = [2, 1];\
13 = [0, 0, 0, 0, 0, 1];


#### "Epimoric factors" of natural integers (integer as a product of ((p+1)/p)<sup>n</sup>):
1 = [0];\
2 = [1];\
3 = [1, 1];\
4 = [2];\
5 = [2, 0, 1];\
6 = [2, 1];\
7 = [2, 1, 0, 1];\
8 = [3];\
9 = [2, 2];\
10 = [3, 0, 1];\
11 = [3, 0, 1, 0, 1];\
12 = [3, 1];\
13 = [3, 1, 0, 0, 0, 1];

Integers can also be written as a product of (p/(p+1))<sup>n</sup>.\
I think it's a cool mathematical concept and I didn't see it used anywhere outside of my composition "Epimoric Music".
### Detuning
The script also enables octave stretching and detuning of individual keys, making it a cool playground for temperament exploration.