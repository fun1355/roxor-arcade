asdf
# Introduction #

Placeholder page for now. This will make more sense with graphics, so I will upload the sketches later.

# Game Design #

The goal of the game is to set a specified register to a specified value. E.g. at the top of the screen it will say "Set EAX = 0xcafebabe"

The basic design is that you have two cliffs, one on the right side of the screen, and one on the left. On the left side, a little man is slowly pushing blocks off the cliff. The blocks are labeled with hex values. He is **push** ing these blocks onto the stack. :)

On the right hand side of the screen, there is another little man, pushing blocks of the cliff. However, those blocks are labeled with assembly instructions. Things like "add eax,ebx", "mov ecx, ebx", "pop ecx". If the user clicks on say the "pop ecx" instruction in the pile on the right side of the screen, the block will disappear, and the top value of the stack on the left side of the screen will disappear (crumble? bounce/ **pop** off the top of the stack?) and go into the relevant register. The register values would be beneath the cliff or built into the cliff or somesuch.

So the point is that the student would need to click the right order of instructions in order to set the specified register value. (They can click to execute them in any order, but they can usually only pop off the top of the stack.)

As the game progresses, of course the blocks fall faster and it requires more instructions to achieve the specified register value.

Round 1: it only takes a single instruction because you will get values which require no math, and you will get all pop instructions.

Round 2: It now takes 2 instructions, e.g. a pop (which will not move into the target register) and then a mov instruction.

Round 3: It now takes 2 instructions but you will have to wait for one of them, it will not be in the initial set.
etc

# Code Repository Path #

This will be filled in when development has begun.