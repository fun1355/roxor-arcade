# Introduction #

Probably a wizardry theme to go with the dark (mathe)magic motif.


# Game Design #

This would be a fairly straightforward game of taking some input register values, and a randomly generated assembly snippet and and asking the user for the value in a register at the end (with the amount of points depending on how fast they answer it.) So you might have something like:

mov eax, 0x4000

mov ebx, 0x50

sub ebx, eax

"What is the value of eax at the end of this code?"
or
"What is the value of ebx at the end of this code?"

And then the user would input the value.

So this would involve increasing complexity by adding new instructions and leading up to moving values out to memory moves including the r/m32 form, and even allowing for the option to answer "not enough information" if the instruction sequence maybe reads some memory location which we don't know anything about. The randomized instructions could reuse the format specifiers from [WhackASsembly](WhackASsembly.md)

# Code Repository Path #

http://code.google.com/p/roxor-arcade/source/browse/trunk/DarkMathemagic