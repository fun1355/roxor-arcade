# Way Of The Byte #

Mostly right now this page is a placeholder because I wanted to claim the excellent title "Way Of The Byte" for this RPG :)

The idea of the game is to show the different skill areas that security professionals can develop over their career, ideally very closely mirroring the real world.

Ideally we would want the elements of the game to teach real world skills (1337 edition), but I also wouldn't mind a game-y abstracted version (n00b edition), just to get people familiar with the breadth of topics in the area.

# Game Design #

## Character Classes ##

There should be a few different character starting classes such as system administrator (specialization of host-defender and network-defender), vulnerability researcher (specialization such as embedded systems, OSes, web applications), etc. Still debating whether to have malicious classes too. Leaning toward inclusion since it's important for defenders to know how attackers work.

Characters would need to gain some basic security background knowledge before they could progress into specialization areas. Things like lessons on confidentiality, integrity, availability.

## Skill Trees ##

Reverse engineer tree:<br>
1)Programming<br>
2)Decompiling (costs more money ;))<br>
2)Disassembling (cheaper skill path ;))<br>
3)Debugging<br>
4)PE format<br>
4)ELF format<br>
4)Mach-o format<br>
Malware analysis tree:<br>
1) Behavioral analysis<br>
2) Document analysis: pdf<br>
2) Document analysis: office<br>
2) Web analysis: flash<br>
2) Web analysis: javascript<br>
(could branch to RE tree from here, but then also unlock additional things such as)<br>
5)Unpacking<br>
6)Anti-anti-debug tricks<br>
6)Anti-anti-VM tricks<br>
6)Anti-anti-dump tricks<br>
7)Advanced unpacking<br>

It would be interesting if there was a game mechanic where your oldest skills became obsolete eventually. This would for instance discourage against over-investment in early skills which would eventually become inaccessible. That's assuming you were using a skill system where you could put multiple points into the same skill.<br>
<br>
<h2>Example Teaching Units</h2>

The below are examples of how gameplay might progress in terms of a back-and-forth between learning new attack and defense mechanisms (playing from either side.) It would also ideally give a sense of which side has the upper hand in a particular domain, and where the endgame is at the moment.<br>
<br>
If you are playing as the system administrator class you would start with a wide-open, flat network. You could do things like adding a border firewall, creating a DMZ, create internal network segmentation, etc.  For your hosts you could invest resource points in configuration/patch management, AV, HIPS, host-based firewall, behavioral analysis, application whitelisting, DLP and other endpoint protection mechanisms. There should be some sort of user disgruntlement meter too where if you throw everything on the endpoint the system gets really slow, the number of errors increases, and the users eventually revolt :)<br>
<br>
<h3>Exploit Development</h3>

This is a good example of how a defender could learn a lot more about how the defensive mechanisms work by seeing how attackers bypass them.<br>
<br>
Learn about canonical stack overflow...<br>
"Oh no, it can be stopped with stack cookies! Progress to..."<br>
Learn about SEH overwrites...<br>
"Oh no, it can be stopped with non-executable memory! Progress to..."<br>
Learn about return to libc...<br>
"Oh no, it can be stopped with ASLR! Progress to..."<br>
Learn about problems with various ASLR implementations...<br>
"Oh no, this ASLR implementation is decent! Proceed to..." <br>
Learn about information leaks<br>
...<br>
Learn about heap overflows...<br>

<h3>Network Scanning</h3>

The module could use a real tool like nmap starting with the simplest possible interface, and as you progress you "unlock" new options and gain experience points. The game could work by using tcpreplay to just play back real traffic to give nmap the results you want.<br>
<br>
Learn about TCP SYN scanning...<br>
"Oh no, it can be blocked by firewall! Progress to..."<br>
Learn about TCP ACK scanning...<br>
"Oh no, it can be blocked by better firewall! Progress to..."<br>
Learn about TCP FIN scanning...<br>
etc<br>
Learn about TCP-based OS fingerprinting...<br>
"Oh no, there's no TCP ports open! Progress to..."<br>
Learn about ICMP-based OS fingerprinting...<br>
"Oh no, there's no ICMP ports open! Progress to..."<br>
Learn about passive OS fingerprinting...<br>
"Oh no, you've moved to a switched network! Progress to..."<br>
Learn about ARP poisoning, enter new man-in-the-middle unit<br>

<h3>Cryptography</h3>

Learn about one-time pad...<br>
"Oh no, keying is a pain in the ass!" Progress to...<br>
Learn about substitution ciphers<br>
"Oh no, it can be attacked with frequency analysis!"<br>
Break example with frequency analysis, then progress to...<br>
Learn about poly-alphabetic ciphers<br>
"Oh no, it can be attacked with Kasiski examination!"<br>
Break example with Kasiski examination, then progress to...<br>
TBD<br>
Learn about DES ECB mode...<br>
"Oh no, ECB mode always generates the same ciphertext for the same plaintext! Progress to..."<br>
Learn about <br>
...<br>
Learn about 3DES.<br>
...<br>
Learn about AES<br>
etc<br>
Learn about known plaintext, chosen plaintext, chosen ciphertext, etc attacks<br>
<br>
<h3>Stealth Malware</h3>

<h1>Code Repository Path</h1>

To be filled in when development begins.