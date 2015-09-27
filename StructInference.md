# Introduction #

A common activity in reverse engineering is inferring the nature of structures used by code. For instance what are the types of the fields? Are the structures organized into higher level data structures such as arrays, linked lists, or binary trees? What additional information can the student describe about how the structure is used?

# Game Design #

The point of this game would be to randomly generate code with random data structure types, and then ask the student to look at the assembly for purposes of answering some final quiz questions. E.g. you could ask the student to define the structure either in terms of a C definition, or you could ask them to graphically edit it by first resizing to the right size, and then partitioning the internal members, and then assigning types to the internal members. Then there could be questions such as "are the structs used in any of the following data structures: array, linked list, binary tree, none of the above?" (and the student could pick multiple answers if the code ever got complicated enough to use multiple.)

# Code Repository Path #

To be filled in when development begins.