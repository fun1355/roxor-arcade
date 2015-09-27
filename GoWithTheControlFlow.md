# Introduction #

This would sort of be the inverse of ["One Step Forward, Three Steps Back"](http://code.google.com/p/roxor-arcade/wiki/1Step3Step), in that you're going forward in the instructions instead of backwards. Picture a racing game where you're going around a track and picking up power ups etc. In this game you go around the track and pick up register values and CMP or TEST instructions (or possibly arithmetic instructions like add which have flag side effects). So you run over an "MOV EAX, 0x1234" and then you run over an "MOV EAX, 0x1234" and then you run over a "CMP EAX, EBX". Then you are driving for a amount of time which decreases as the difficulty goes up, and you get to a sign which says something like "<- JNE, JE ->" which is basically trying to say that if you would hit a JNE instruction, and if you would follow it based on the compare (that is, if the ZF != 1), you should steer your car to the left, otherwise the right. If you steer your car down the false branch, you will crash and die in a variety of amusing ways :)

# Game Design #

You can probably reuse some of the logic from ["One Step Forward, Three Steps Back"](http://code.google.com/p/roxor-arcade/wiki/1Step3Step), because fundamentally you need to do the same process of generating a sequence of assembly instructions and knowing a-priori whether it will evaluate to true or not. The main difference is that this inherently has to be a graphical race game to be cool :)

# Code Repository Path #

To be filled in when development starts