# Introduction #

The first thing worth noting is that there already exists a game by Cisco which helps teach people about binary to decimal conversion, and vice-versa.
http://forums.cisco.com/CertCom/game/binary_game_page.htm

While this is a good game, hexadecimal (base 16, 0 through 9 and A through F (representing 10 through 15) is the radix which people most often look at numbers in when disassembling code. And it is hexadecimal to binary conversion which is used very often when understanding flag-setting/clearing behavior in code.


# Game Design #

I envision something like a binary/hex/dec value being displayed and then an arrow bouncing back and forth between hex and decimal before ultimately settling on one or the other (based on random value being [0,.5) or [.5,1))

Then the user needs to type in the appropriate translation to whichever was picked.

Then they get a bonus if they can type in the other translation which wasn't initially picked in under some amount of time. Obviously the points you get is based on time, and as the rounds go on, the translations get harder (e.g. more odd numbers), and then the clock ticks down faster.

Also the selection of which of the 3 the starting value is in will be randomized later in the game (whereas it may be fixed to start with where you have one round of all binary->hex/dec, one round of all hex->bin/dec, one round of all dec->bin/hex)

# Code Repository Path #

http://code.google.com/p/roxor-arcade/source/browse/trunk/BinDeciHex/perldemo/