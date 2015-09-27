# Introduction #

This game is being developed specifically for the 2012 edition of [Life of Binaries](http://opensecuritytraining.info/LifeOfBinaries.html)


# Game Design #

The core of the game is a script which is able to randomly generate a series of binaries (PE to start with, ELF later).

There will be a series of levels, which correspond to sections of the Life of Binaries class material. E.g.

Level 1: DOS & NT File Header

Level 2: NT Optional Header & Data Directory

Level 3: Section Headers

Level 4: Imports "Regular"

Level 5: Imports: Bound/Delay Load

Level 6: Exports

Level 7: Debug Info & Relocations

Level 8: Thread Local Storage callbacks

Level 9: Resources

Level 10: Load Configuration & Signed Code


For each level, right after the class covers a topic, the student will get say 10 questions about the content, with 5 randomized questions being about the current content, and 5 questions being from the previous content areas. They will be questions like "According to the file header TimeDateStamp, what year was this binary compiled?", "How many sections does this binary have?", "How many DLLs does this binary import functions from?", or "At what address will this code start executing?" (which will change such that they have learned about TLS callbacks, and they need to check for TLS callbacks.) The answers would either be in the form of a single yes/no/number. And the answers would be derived by using a tool of their choice such as CFFExplorer in order to pull the info out of the binary.

The interesting thing about this class is that we can use seeds to the pseudo random number generator which will pick the binaries and pick the questions, in order to make it so that an entire class gets the same binaries. Then they can compete directly against each other, with built in time bonuses for correct questions. The first person done wouldn't necessarily be the highest score, because they could get stuff right. And even multiple people get them all right there may still be some person who got it right faster and therefore is declared the champion! Then the class could also have like a leader board.

The use of the seed can also allow for head to head competition between 2 or more players. Player 1 can enter how many questions he wants to accept, and then play that many questions pulled from all topics. Once he's done, the program can spit out his score and the initial seed that was used. Then other people could use that same seed and try to beat the score. Of course it's a gentleman's game, because people can always lie about their scores.

# Code Repository Path #

http://code.google.com/p/roxor-arcade/source/browse/trunk/BinaryScavengerHunt/pythondemo