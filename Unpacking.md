# Introduction #

Here the trick is that you need to order packers by increasing difficulty (starting with UPX of course), and then you need to have a source program which is being packed which at the minimum has a randomly changed OEP, so that the goal of each round of the game is to find the OEP. This seems like it could be scripted together pretty easily by just giving appropriate linker options and then sending the file into a series of increasingly difficult packers. And the game can determine whether you're correct or not because it picked the OEP to start with. The only problem of course comes from again having to deal with debugger (and presumably some anti-debug tricks in the harder levels.) Also, this is about the level where I would hope people would start actually just trying to attack the game program.

Ultimately I want it to be the case that in order to **really** win at R0x0r Arcade, you need to "cheat" and go in and give yourself the maximum score by finding and patching wherever the score is being stored. It might taunt people with something like "You are not yet a r0x0r, you have non-maximum score..." :D

# Game Design #

# Code Repository Path #

To be filled in when development begins.