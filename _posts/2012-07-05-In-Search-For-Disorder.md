---
layout: post
title: In Search For Disorder
author: Sławek
---

When Java application running inside virtual machine tries to connect to the Oracle database it can suddenly and seemingly in a completely random moment throw "I/O Exception: Connection reset". At first database driver hangs for a while and after the timeout expires gives up and prints the error. Restart of the application usually does not help.
How to fix this problem?
Launch 'find /' in the console.
The connection suddenly establishes.

So what happens?
Linux system on a virtual machine lacks an entropy. Oracle driver needs a pool of random numbers in order to encrypt its connection. It uses java.security.SecureRandom which in turn reads them from /dev/random file.

But here is what 'man 4 random' says: The random number generator gathers Environmental noise from device drivers and other sources into an entropy pool. [...] When the entropy pool is empty, reads from /dev/random will block until additional Environmental noise is gathered. The best source of randomness in a computer are the physical devices. The problem is that the virtual machine does not have a mouse or a keyboard. After a while hard drive operations are no longer useful either as all data will be cached in the host machine. Firing 'find /' helps because it forces the system to read something new from the disk immediately gathering some entropy. But this is only one time workaround.

______

To solve the problem you can soft link '/dev/random' file to point to '/dev/urandom'. You can also direct Java VM to use urandom by adding the following property: '-Djava.security.egd=file:/dev/urandom'. But there is a cost. Although '/dev/urandom' never blocks it might return numbers which are not truly random.

Where to find real randomness? In the processor. It turns out you can write the code which execution time is not always consistent. There is a measurable uncertainty introduced by internal mechanics of the processor. This trick was used to write the daemon named haveged. Haveged can continuously generate several megabytes of random data per second. For a comparison the the stock Linux kernel generator usually produces no more than a few dozen bytes per second.

Links:


Oracle 11g JDBC driver hangs blocked by /dev/random – entropy pool empty
JDBC Connection Reset when using many processes on 64 bit system
