# Endian's Game #

I remember that when I was first learning little endian as it applies to Intel architecture, I occasionally got confused about whether it applied to every bit, or just bytes, or just 4 byte values or what. Therefore this game would leave absolutely no uncertainty about how it applies. It can also reinforce that if you're not seeing it by virtue of using some other computer architecture besides Intel, you will see it due to network ordering being big endian.

# Game Design #

This game will feature a stick figure tucked into a crouch, freefalling in one of the four cardinal directions on the screen. The top of the screen will say "The enemy is _Little Endian_ _0xDEADBEEF_" (where the endianness and hex constant can change). Then as the user is falling, he will have to navigate (with the cheater help of a little jetpack, sorry, we can't be 100% accurate ;)) and make sure he shoots the hex which is coming toward him, but only the hex which is in the specified endianness and the specified constant.

As the levels progress, the user will change from only falling down to "falling" left, right, or up. But the user has to keep the endianness principle in mind, and has to keep navigating and shooting the right constants as the levels speed up.

A notional picture will be posted to help give a better sense of this game. Anyone who knows HTML5 or flash game development is asked to help volunteer for this.

# Code Repository Path #

To be filled in when development starts