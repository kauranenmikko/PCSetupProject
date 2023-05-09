# PCSetupProject
A small salt project to setup a baseline PC for Linux and Windows.

## What is the aim

Debian comes with pretty much nothing installed. 

Windows comes with _too much_ crap installed.

The idea is to make a single script/file that will setup either a linux or a windows installation with programs that I will use, while also cleaning up unneeded stuff.

## Prerequisites

Salt installed on the system.

Sudo/Administrator rights on the target PC.

Windows requires Pro/Enterprice version for Group Policy changes, you can probably? have it work on other versions by manually installing gpedit.msc beforehand but ¯\\__(ツ)__/¯
