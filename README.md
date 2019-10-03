# tcpping v2.x

## fork of elder tcpping v1.8 script running with newer traceroute binary

This script is a fork of Richard Van de Berg's tcpping script, original version found [here](https://github.com/deajan/tcpping/tree/original-1.8), supporting newer traceroute binaries.
Usage is the same and should work out of the box for smokeping.

It comes with various improvements like language agonstic functionality, better error detection, debug, and removed tcptraceroute dependancy.

So far, tests have been done with:
- CentOS 7: v2.0-2.3 tested (with traceroute 2.0.22 and bash 4.2.46(2)-release)
- CentOS 8: v2.3 tested (with traceroute 2.1.0 and bash 4.4.19(1)-release)
- FreeBSD 11.2: v2.0-2.3 tested (with traceroute 1.4a12 and tcsh 6.20.00)
Also, smokeping 2.7.2 and 2.7.3 have been tested.

## Installation

`sudo wget -O /usr/bin/tcpping https://raw.githubusercontent.com/deajan/tcpping/master/tcpping ; chmod 755 /usr/bin/tcpping`

## Usage

Example command smokeping would use

`tcpping -C -x 5 myhost 80`

Example command for sub second tcp ping analysis on Linux

`tcpping -x 10 -w .1 -o myhost 443`

Keep in mind that the tcp / udp probe checks for a SYN flag, which does not mean that a service is listening on the target machine port.

## Root privileges

By default, traceroute needs root privileges.
You may launch script with sudo or with '-Z' in order to ask for root privileges during execution.
By doing so, you may edit your sudoers file by allowing user 'bob' to run traceroute as root without password
```
bob ALL=(ALL) NOPASSWD: /usr/bin/traceroute
```

## Licence and improvements

Altough there are probably better tools out there (hping, nmap, etc), this is still a quick and handy tool used by smokeping, so every improvement / fork / pull request is more than welcome.

Originally, Richard linked to the GPLv2 licence.
Having talked with him, he did allow to update to GPLv3, so this script is GPLv3.
