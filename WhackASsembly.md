# Introduction #

This is inherently a whack-a-mole skin for what is a flash card memorization game of learning what the various x86 (or any other instruction set, if ported) instructions are. (I really want a Number Munchers skinning of such a game if you ever played that as a kid ;))

How the skin works is that at the top of the screen there is some directive for which types of Moles-with-assembly-instructions-on-their-heads you are supposed to whack.

The reason for going with a whack a mole skin is because then there's the option to increase speed as time goes on. Also between rounds is when the player is introduced to the various instructions by a guide character. Picture the board consisting of 7 mole holes stretched out horizontally.

# Game Design #

Round 1:
The top of the screen will say a broad category like "move instructions", "call instructions", "conditional jump instructions" etc. Then when each mole pops up, it will have a randomized, programmatically generated instruction above its head.

Round 2:
Stuff gets more specific in that you have things like "Move memory to register" or "Move Immediate to memory" etc. Then you get randomized things within some set (like move) which then make the person pay more attention to the operands of the instruction, rather than the opcodes.

I believe that most of the randomization for the instructions can be achieved by creating format strings for whatever forms of the instructions are available. Also then you need to specify the kind of descriptions which will be put to the student for each level. For example in x86:

```
%i = 32 bit immediate
%i8 = 8 bit immediate
%i16 = 16 bit immediate
%r = 32 bit register
%r8 = 8 bit immediate
%m = memory location specifying a 32 bit value
%m8 = memory location specifying a 8 bit value



---------------------Level 1---------------------

instruction		summary			detailed

add %r, %r		addition		add register to register, store result in left register (Intel syntax)
add %r, %m		addition		add memory to register, store result in register
add %m, %r		addition		add register to memory, store result in memory

sub %r, %r		subtraction		subtract right register from left register, store result in left register (Intel syntax)
sub %r, %m		subtraction		subtract memory from register, store result in register
sub %m, %r		subtraction		subtract register from memory, store result in memory

mul %r			multiply		unsigned multiply edx:eax <- eax*register
mul %m			multiply		unsigned multiply edx:eax <- eax*memory
imul %r			multiply		signed multiply edx:eax <- eax*register
imul %m			multiply		signed multiply edx:eax <- eax*memory
imul %r, %r		multiply		signed multiply register <- register * register
imul %r, %m		multiply		signed multiply register <- register * memory
imul %r, %r, %i		multiply		signed multiply register <- register * immediate
imul %r, %m, %i		multiply		signed multiply register <- memory * immediate

div %r			divide			unsigned divide edx:eax by register, eax<-quotient, edx = remainder
div %m			divide			unsigned divide edx:eax by memory, eax<-quotient, edx = remainder
idiv %r			divide			signed divide edx:eax by register, eax<-quotient, edx = remainder
idiv %m			divide			signed divide edx:eax by memory, eax<-quotient, edx = remainder

and %r, %i		bitwise AND		AND register and immediate, store result in register
and %r, %r		bitwise AND		AND register and register, store result in left register (Intel syntax)
and %r, %m		bitwise AND		AND register and memory, store result in register
and %m, %r		bitwise AND		AND memory and register, store result in memory
and %m, %i		bitwise AND		AND memory and immediate, store result in memory

or %r, %i		bitwise OR		OR register and immediate, store result in register
or %r, %r		bitwise OR		OR register and register, store result in left register (Intel syntax)
or %r, %m		bitwise OR		OR register and memory, store result in register
or %m, %r		bitwise OR		OR memory and register, store result in memory
or %m, %i		bitwise OR		OR memory and immediate, store result in memory

xor %r, %i		bitwise XOR		XOR register and immediate, store result in register
xor %r, %r		bitwise XOR		XOR register and register, store result in left register (Intel syntax)
xor %r, %m		bitwise XOR		XOR register and memory, store result in register
xor %m, %r		bitwise XOR		XOR memory and register, store result in memory
xor %m, %i		bitwise XOR		XOR memory and immediate, store result in memory

not %r			bitwise NOT		invert (one's compliment) every bit in register
not %m			bitwise NOT		invert (one's compliment) every bit in memory

neg %r			negate			two's complement the value in a register
neg %m			negate			two's complement the value in memory

mov %r, %r		move			move value in right register to left register (Intel Syntax)
mov %r, %m		move			move memory to register
mov %m, %r		move			move register to memory
mov %r, %i		move			move immediate to register
mov %m, %i		move			move immediate to memory
mov %r, %cr		move			move control register to register (*trivia)
mov %cr, %r		move 			move register to control register (*trivia)
mov %r, %dr		move			move debug register to register (*trivia)
mov %dr, %r		move			move register to debug register (*trivia)

lea %r, %m		load effective address	load address of given memory location into register

jmp %rel8		jump			jump short, relative, within +127 to -128 bytes from the end of the instruction
jmp %rel32		jump			jump near, relative, within (+)0x7FFFFFFF to (-)0x80000000 bytes from the end of the instruction
jmp %r			jump			jump near, absolute indirect, jump to the address specified by the register
jmp %m			jump			jump near, absolute indirect, jump to the address specified by the memory
jmp %sr:%i		jump			jump far, absolute, jump to the absolute offset in the segment specified by the segment register (*trivia)
jmp %m16:m32		jump			jump far, absolute indirect, jump to the absolute offset in the segment specified by a 48 bit value in memory comprising a 16 bit segment selector and 32 bit offset (*trivia)

call %rel32		call			call near, relative, within (+)0x7FFFFFFF to (-)0x80000000 bytes from the end of the instruction
call %r			call			call near, absolute indirect, call to the address specified by the register
call %m			call			call near, absolute indirect, call to the address specified by the memory
call %sr:%i		call			call far, absolute, call to the absolute offset in the segment specified by the segment register (*trivia)
call %m16:m32		call			call far, absolute indirect, call to the absolute offset in the segment specified by a 48 bit value in memory comprising a 16 bit segment selector and 32 bit offset (*trivia)

ret			return			return from procedure
ret %i16		return			return from procedure and pop the immediate number of bytes from stack

push %i			push			push immediate
push %r			push			push register
push %sr		push			push segment register (*trivia)
push %m			push			push memory

pop %r			pop			pop to register
pop %sr			pop			pop to segment register (*trivia)
pop %m			pop			pop to memory (*trivia)

---------------------Level 2---------------------

pusha			push			push all general purpose registers (16 bit forms)
pushad			push			push all general purpose registers (32 bit forms)
pushf			push			push FLAGS register
pushfd			push			push EFLAGS register

<Add in the smaller form general purpose registers>

add %r8, %i8		addition		add 8 bit immediate to 8 bit register, store result in 8 bit register
add %m8, %i8		addition		add 8 bit immediate to 8 bits specified by memory location, value changed in memory
add %r8, %r8		addition		add 8 bit register to 8 bit register, value changed in left register
add %m8, %r8		addition		add 8 bit register to 8 bits specified by memory location, value changed in memory
add %r8, %m8		addition		add 8 bits specified by memory location to 8 bit register, value changed in register

sub %r8, %i8		subtraction		subtract 8 bit immediate to 8 bit register, store result in 8 bit register
sub %m8, %i8		subtraction		subtract 8 bit immediate to 8 bits specified by memory location, value changed in memory
sub %r8, %r8		subtraction		subtract 8 bit register to 8 bit register, store result in left 8 bit register
sub %m8, %r8		subtraction		subtract 8 bit register to 8 bits specified by memory location, value changed in memory
sub %r8, %m8		subtraction		subtract 8 bits specified by memory location to 8 bit register, value changed in register

and %r8, %i8		bitwise AND		bitwise AND 8 bit immediate with 8 bit register, store result in 8 bit register
and %m8, %i8		bitwise AND		bitwise AND 8 bit immediate to 8 bits specified by memory location, value changed in memory
and %r8, %r8		bitwise AND		bitwise AND 8 bit register to 8 bit register, store result in left 8 bit register
and %m8, %r8		bitwise AND		bitwise AND 8 bit register to 8 bits specified by memory location, value changed in memory
and %r8, %m8		bitwise AND		bitwise AND 8 bits specified by memory location to 8 bit register, value changed in register

or %r8, %i8		bitwise OR		bitwise OR 8 bit immediate with 8 bit register, store result in 8 bit register
or %m8, %i8		bitwise OR		bitwise OR 8 bit immediate to 8 bits specified by memory location, value changed in memory
or %r8, %r8		bitwise OR		bitwise OR 8 bit register to 8 bit register, store result in left 8 bit register
or %m8, %r8		bitwise OR		bitwise OR 8 bit register to 8 bits specified by memory location, value changed in memory
or %r8, %m8		bitwise OR		bitwise OR 8 bits specified by memory location to 8 bit register, value changed in register

xor %r8, %i8		bitwise XOR		bitwise XOR 8 bit immediate with 8 bit register, store result in 8 bit register
xor %m8, %i8		bitwise XOR		bitwise XOR 8 bit immediate to 8 bits specified by memory location, value changed in memory
xor %r8, %r8		bitwise XOR		bitwise XOR 8 bit register to 8 bit register, store result in left 8 bit register
xor %m8, %r8		bitwise XOR		bitwise XOR 8 bit register to 8 bits specified by memory location, value changed in memory
xor %r8, %m8		bitwise XOR		bitwise XOR 8 bits specified by memory location to 8 bit register, value changed in register

cmp %r8, %i8		compare			subtract 8 bit immediate to 8 bit register, set flags but don't store value
cmp %m8, %i8		compare			subtract 8 bit immediate to 8 bits specified by memory location, set flags but don't store value
cmp %r8, %r8		compare			subtract 8 bit register to 8 bit register, set flags but don't store value
cmp %m8, %r8		compare			subtract 8 bit register to 8 bits specified by memory location, set flags but don't store value
cmp %r8, %m8		compare			subtract 8 bits specified by memory location to 8 bit register, set flags but don't store value
cmp %r, %r		compare			subtract right register from left register, set flags but don't store value
cmp %r, %m		compare			subtract memory from register, set flags but don't store value
cmp %m, %r		compare			subtract register from memory, set flags but don't store value

test %r8, %i8		test			bitwise AND 8 bit immediate with 8 bit register, set flags but don't store value
test %m8, %i8		test			bitwise AND 8 bit immediate to 8 bits specified by memory location, set flags but don't store value
test %r8, %r8		test			bitwise AND 8 bit register to 8 bit register, set flags but don't store value
test %m8, %r8		test			bitwise AND 8 bit register to 8 bits specified by memory location, set flags but don't store value
test %r8, %m		test			bitwise AND 8 bits specified by memory location to 8 bit register, set flags but don't store value
test %r, %i		test			bitwise AND register and immediate, set flags but don't store value
test %r, %r		test			bitwise AND register and register, set flags but don't store value
test %r, %m		test			bitwise AND register and memory, set flags but don't store value
test %m, %r		test			bitwise AND memory and register, set flags but don't store value
test %m, %i		test			bitwise AND memory and immediate, set flags but don't store value

div %r8			divide			unsigned divide ax by 8 bit register, al<-quotient, ah = remainder
div %m8			divide			unsigned divide ax by 8 bit value in memory, al<-quotient, ah = remainder
idiv %r8		divide			unsigned divide ax by 8 bit register, al<-quotient, ah = remainder
idiv %m8		divide			unsigned divide ax by 8 bit value in memory, al<-quotient, ah = remainder

mul %r8			multiply		unsigned multiply ax <- al * 8 bit register
mul %m8			multiply		unsigned multiply ax <- al * 8 bit value in memory
imul %r8		multiply		signed multiply ax <- al * 8 bit register
imul %m8		multiply		signed multiply ax <- al * 8 bit value in memory
imul %r, %i8		multiply		signed multiply register <- register * 8 bit immediate (FIXME: did this go away between 2008 and 2009 manual, or am I just reading it wrong?)

```

# Code Repository Path #

To be filled in when development begins.