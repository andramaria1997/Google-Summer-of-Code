Google Summer of Code
================================================

Project: ASoC codec driver
The goal of this project is to write a driver for I2S Stereo Decoder - UDA1334A

Code license: GPL
Development board: PICO-PI-IMX8M

--------------------------------------------------------------------------------

# The journey begins

Hello, World!

Since we are going to take this journey together, let’s get to know each other
better! I’m a 3rd year Romanian student pursuing a Computer Science degree,
probably just like any other student part of Google Summer of Code program.

My first interaction with open-source community was becoming a Romanian
Open-Source Education member, 7 months ago. I got involved in promoting and
organizing open-source related events and I started to feel like I’m part of
more than just an organization: a strongly connected community. The idea of
open exchange, collaborative participation and community-oriented development
makes me feel like I’m part of a huge family of which every software developer
in this world is a part of. I believe that ideas should be available to others
and shared with everyone, not held private. I believe that the process of
software developing should be brainstorming, not independent.

I found out about this program from other students at my university that
participated at past GSoC editions, so I wanted to join. Here I am today, about
to start working at a driver for a stereo decoder which, if successful, is
going to be accepted into Linux kernel ASoC maintainer’s tree.

Wish me luck!

--------------------------------------------------------------------------------

# First baby steps

Hello, World!

Thank you for coming back!

I’m going to talk about my first steps into Linux Kernel programming and how
I started to prepare myself for working on the project, considering the fact
that I’ve never done kernel programming before. The first thing to do was,
obviously, take a look at some tutorials. At my university, Operating Systems
course is split into two main courses, the first one on user space programming
and the second one on kernel space programming. So, I chose to solve a part of
the latter course’s
[`laboratories`](https://linux-kernel-labs.github.io/master/labs/introduction.ht
ml). What is more, I slowly started to read [`Linux Device Drivers – Where
kernel meets the driver`](https://www.oreilly.com/openbook/linuxdrive3/book/).

I learned to work with kernel structures, to write and compile modules and how
a driver interacts with a device through a device file. I found the way that
“content_of” macro makes the elegant kernel design of linked lists possible
really impressive. It is one of the most intelligent usage of Data Structures
I’ve ever seen. I don’t know yet how exactly this black magic sorcery works,
but be sure I’ll find out.

Also, about the non-tech part of Google Summer of Code experience, Community
Bonding period was quite pleasant. I got to know my mentor Daniel Baluta better
and thanks to him I tried Indian food for the first time. :)

See you next time! 😀

--------------------------------------------------------------------------------

# Basic booting of IMX8-MM-PICO

Hello, World!

Glad to see you again!

It’s been one month since the coding period for GSoC 2019 started, so it’s time
to show the world the progress I made. First things first, the hardware came
with linux kernel version 4.9 installed, which was not the latest version, so,
too old to start to work on the driver. Therefore, the first thing to be done
was to boot linux-next kernel on it. Challenge: find a way to do it, since the
board had no SD card slot attached and I was not brave enough to overwrite
something that boots, risking to end up with nothing functional. So, what I
chose to do was to compile kernel Image locally on my machine(x86 architecture)
for imx8-mm-pico-pi (arm64 architecture) in FIT format, load it in board's RAM
memory, then boot it from there.

![loadimage](https://github.com/andramaria1997/gsoc/blob/master/images/loadimage.png)

Aaand success! :D

![firstboot](https://github.com/andramaria1997/gsoc/blob/master/images/firstboot.png)

I wrote a small tutorial on [`how to boot linux-next on 
imx8-mm-pico`](https://github.com/andramaria1997/gsoc/blob/master/boot-linux-next.md)
the way I did.

Ethernet and USB are functional. From now, I guess I can start working on the
driver.
