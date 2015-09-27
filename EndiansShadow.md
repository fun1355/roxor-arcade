# Endian's Shadow #

I finally thought up a good graphical paradigm for [Endian's Game](EndiansGame.md), so this weaker and quicker to develop version will be Endian's Shadow. The intent still is to help people get their head on straight for endianness.

# Game Design #

This will just show a hex dump 16 bytes wide and give the user a offset into the dump (probably 0x4 byte aligned at the beginning and not aligned later). To start with the hex dump would be assumed to be on a little endian system like x86, and the user would be asked to give the big endian value at some offset. In later rounds it would change to  incorporate some instructions and some registers. First it would try to reinforce the fact that the values are always displayed in big endian in the registers by asking questions like "if you moved the data at offset 0xC into register eax, what would eax show?". And then it would incorporate actual instructions like "mov eax, [ebp-0xC]. what is eax?"

# Code Repository Path #

To be filled in when development starts