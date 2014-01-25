---
layout: post
title: A few words in ASCII about ASCII
author: Sławek
---
_The following text was written to celebrate the 50th anniversary of establishing the ASCII code_.

As recently as yesterday I lost an hour of my miserable existence trying to find the reason for unit test failures under Windoze. The time all the more unpleasant because of my innate aversion to this system. The problem turned out to be the difference in the encoding of the line endings... I fixed it immediately for hax not to wait any more... 

However at this point I imagined the voice of our Scrum masters yelling at me: 5 x Why!

* Why the test failed? Because I did not realize the difference in line encoding.
* Why the line is encoded differently? Because the ASCII code has two separate line ending symbols and different software creators chose one or the other.
* What a moron invented two different line endings?

To calm down let's go back to year 1961 AD. Nothing pleases more than the realization that one day people suffered more. It was a time when every computer model had its own unique character encoding system. There were about 60 different systems in use of which 9 where invented at IBM. It was therefore not that much surprising that finally a committee gathered which after a whopping two (say two) years of debates assigned 100 characters to a seven bit numbers (28 codes were left not assigned). Long time for a numbering of a few letters, but every hardware manufacturer wrangled about the position of the smallest comma to make sure they don't need to modify their devices too much. So, in 1963 the ASCII was born.

The new standard, however, had not an easy way to adoption, because in the meantime IBM, the main proponent of ASCII, unwilling to wait, introduced in-house designed EBCDIC system... EBCDIC had only one character for the end of line :-)
Unfortunately, in 1968 the U.S. President signed a decree that the only right system is ASCII. Soon after, the Brits also adopted a system by adding, who would have thought, the encoding for the pound sterling.

But it was not the ASCII which defined two line ending characters for the first time. Standardization committee just copied this "invention" from the earlier standard - Baudot code. Baudot code was designed in 1870 and replaced Morse code for telegraph transmissions. It enabled the use of devices called teletypewriters (in short TTY, you know /dev/tty, don't you?). Directly responsible for two line endings is Donald Murray, who in 1901 updated Baudot code adding two characters: CR - which ordered printing head of the teletypewriter to return to the left side, and LF for moving the paper one line up!
CP/M, MS-DOS and finally Windows adopted CR-LF pair. Multics, and then every Unix adopted only LF with in-driver conversion when the attached printer required it.

To summarize, the blame for my bug goes to Donald Murray for inventing two separate line endings, president Lyndon B. Johnson who forced everyone to use it and Massachusetts Institute of Technology for skimping one character. Thank You all!

Bibliography:
* [https://www.rfc-editor.org/EOLstory.txt](https://www.rfc-editor.org/EOLstory.txt)
* [http://ascii-world.wikidot.com/history](http://ascii-world.wikidot.com/history)
* [https://en.wikipedia.org/wiki/ASCII](https://en.wikipedia.org/wiki/ASCII)
* [https://en.wikipedia.org/wiki/Newline](https://en.wikipedia.org/wiki/Newline)
