# Introduction #

The point of this game is to get to the essence of reverse engineering, which in my mind is taking some assembly instruction and understanding what its implications are, and then walking backwards to see from what inputs the implications are derived.

# Game Design #

Here you would generate a random assembly conditional (as given by the relevant flags like ZF==0,CF==1, etc). Then, you would randomly decide if you want it to be true, or not true. From there you would turn the conditional into a jcc instruction like JZ or JB.  From there you would then generate 1-2 instructions which would be placed before the jump which would either force the condition to be true or false, depending on what you picked in the previous stage (I would probably just start with a fixed set of preceding instructions to start with, and just randomize constants and registers). So you would end up with something like

```
xor eax, eax
jz <bla>

or 

mov eax, 0x1234
sub eax, 0x1235
jb <bla>
```

And then the question for each sequence would be "Will the jump be taken?" and the user needs to answer yes or no. In order to compensate for the fact that they would otherwise have a 50/50 chance of getting it right, they will be penalized twice as much for a mistake as they will get for a correct answer.

Inside of the rounds in this sub-game, we would eventually increase the number and complexity of instructions. We would also start randomizing which mnemonic things are known as (JZ vs. JE, JB vs. JNAE, etc).

sub-game 2:
In this stage, we then start asking the user to input values in order to force a conditional one way or the other. So for instance you might be presented with the sequence

```
mov eax, ebx
sub eax, 0x1235
jb <bla>
```

And the prompt will read "Give a value for ebx to make the jump be taken" or it could say "not be taken". So clearly this requires a bit more complexity in that now we have a range of values the user could input which would potentially be correct.

# Code Repository Path #

http://code.google.com/p/roxor-arcade/source/browse/trunk/1step3step/perldemo/