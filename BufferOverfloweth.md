# Introduction #

A game which programmatically generates vulnerable C code and then compiles, or which just goes straight to a binary (ideally for either ELF or PE). Then the student has to write exploit code for it. While there are plenty of hand-coded examples of vulnerable programs out there, the key distinction of this game would be the fact that it can just keep generating new examples. And the game can also get progressively more difficult to teach one technique at a time.


# Game Design #

Round 1:
You would just have two adjacent buffers, with buffer 1 always being smaller than buffer 2 by at least 2 dwords so that you can always overwrite the saved eip. And the copying will take place with a memcpy() so there are no restrictions on what the user can input. You then will also have a snipped of code which prints "Winner" where the user can see its starting address (or possibly if there is constrained screen space it may just tell them the eip they should use for their target code).

Round 2:
Now the user no longer has an existing target, and he needs to place his code to execute into the buffer, but otherwise everything is the same.

Round 3:
Now you might introduce some other randomly sized local variables inbetween the two buffers. It will then also change from a memcpy() to a strcpy() in order to introduce limits on the characters the user can input.

Round 4:
Ret-to-libc

Round 5:
Generate buffers so that you can only do the ebp 1-byte overwrite

Round 6+:
Start using filters like toupper() or tolower() on any data the student may submit.

# Code Repository Path #

To be filled in when development begins.