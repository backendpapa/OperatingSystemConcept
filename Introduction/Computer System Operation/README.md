# Computer System Operation

### OS Booting Process

1. Switch on the power button
2. The bootstrap program which comes with the PC gets booted.
Bootstrap program is stored in the hardware area called the ```firmware```
3. The bootstrap program locates the Kernel of the OS and loads it into memory.
4. The OS can now provide services to the system and the user.

An OS sits quietly waiting for an event to occur, which is signalled by interrupt.   Another form of interrupt is called ```exception``` or ```trap```. Trap is triggered by a software generated error.
