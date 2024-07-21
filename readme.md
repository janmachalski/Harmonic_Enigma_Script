# Harmonic Enigma Script for Kontakt
##About
This is a KSP scalesmithing script for xenharmonic explorations in Kontakt. This is my swiss knife for manipulating tunings, cales and harmonies inside Native Instruments Kontakt.

##Requirements:
Kontakt v. 6.8 (previous versions might also work but there has been some glitches observed in Kontakt 5).
Setup:
Copy the script code and past it inside Kontakt script editor.
(Unfortunately Kontakt has 5 script slots and sometimes all of them are taken by default. If this is the case, you might have to delete one of the current scripts or redo the instrument whatsover.)

##Why another microtuning script?
I will try to explain my main motivations for writing this script.
###Automation
Most existing scripts are limited in one way or another, mainly in terms of automations. I wanted to be able to automate microtonal tunings freely and change them dynamically. Most of the time user input is done through ui_value KSP objects which do not allow any kind of automation. Midi is limited to 128 note classes. Automation extends the possible number of pitch classes above this limit.
###Transposition
I wanted to be able to freely transpose through different microtonal keys, mainly using common-note transposition. 
###Script linking
You can send MIDI outside of Kontakt and route it to another instance to control the tuning of different instruments from one place. Normally, if you want to change a microtonal tuning you have to do it through pain in every instrument. If you use the linking option of this script, you can manipulate scales and tunings everywhere from one place. E.g. you can modulate to a different key just by turning a single knob, and every other connected instance will follow.
To use this option you have to enable MIDI rpn messages in the Kontakt menu and route MIDI from a "master" instance of Kontakt to every other in your prefered DAW. Note that AU plugins don't support sending MIDI, so you should use vst or vst3 versions of Kontakt.
###Correct zone playback
In all of the scripts I've seen, if you tune a note up by 200c it will play the same zone tuned by 200c even if there exist a separate zone a wholetone above, that could be played with 0 transposition. I want the sampler to execute the nearest zone to a given pitch. It's not a problem in single sample instruments, but when I use a deep-sampled instrument I want to use it's full potential.
###Octave reduction
I wanted to implement different octave reduction methods, e.g. "alias" mode where an interval above an octave is reduced not by an octave but by the interval difference from the octave, e.g. major 10 would go to a minor 6th. I also wanted to implement non-octave systems.
###Adaptive Just Intonation
You can momentarly switch on the adaptive just intonation. It's an experimental feature to allow infinite comma pumps. Basically, you can play triads of the Benedetti's puzzles and the script will calculate the correct pitch drift infinitely.
###Zalewski's harmonic structures
I wanted to implement an automatable calculator for scripting Zalewski's harmonic structures live.
###Epimoric system
I wanted to be able to use a tuning system that I created for my "Epimoric Music" project. I will try to explain it briefly using my limited english vocabulary. The important think is that I enjoy the harmonies that this system proposes. There are some nice prime number sequences that I like to explore musically and geometrically. This system involves combining ratios in a form of (n+m)/m or n/(n+m) where n and m are simple integers. Those look pretty mathematically because the increments of m create consecutive steps of the scale, e.g. pentatonic (5+0)/5; (5+1)/5; (5+2)/5; (5+3)/5; (5+4)/5. I call those variables modus and gradus. Then, starting from any of the pitch classes, i construct a conjunct scale in a same manner. In the composition "Epimoric Music" I used only modus=3. The ratios (n+m)/m are similar to the harmonic mean monochord operations. Ratios in a form of n/(n+m) are similar to the arithmetic mean. I understand harmonic and arithmetic means as otonal and utonal harmonies, that is major-like overtone segments and minor-like undertone (subharmonic) scales. The core of this harmonic system are not the scales themselfs, but the fact, that they are transposed and modulated through common-tones. This is the gist of it. I also use superparticular ratios based on prime numbers (p+1)/p to notate every rational number. It is similar to the Monzoes notation but is based on "(p+1)/p" ratios and not singular "p", e.g. 3=[0,1] in Monzo notation but it's [1,1] in the epimoric one, because 3=(2^0)*(3*1)=((2/1)^1)*((3/2)^1). When writing down natural integers the 'epimoric notation' seems less random than the Monzos (which are simple prime factors), because the total number of factors increases steadly with nearly every integer. I also prefer to think how many octaves (2/1), fifths (3/2) and major thirds (5/4) there are from a given fundamental and not how many 2nd, 3rd and 5th multipliers there are.
