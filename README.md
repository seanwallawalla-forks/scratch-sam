# Hi, I'm S.A.M.! S.A.M. I am!

S.A.M is short for Scratch Advanced Microcomputer.
S.A.M is a fully custom 16-bit ISA (Instruction Set Architecture) + Emulator written using Scratch 3.0. 

# Emulator features
 * It has a built-in MOS 6502-style assembler.
 * It has a AIOC (Advanced I/O Controller) built-in to interface with external Scratch code.
 * 2 64 KiB Memory spaces w/ programmable bank switching

# CPU Features
 * All instructions are big endian format.
 * Simple instruction format.
 * Variable-length instructions.

# How does S.A.M. work?

Starting with initialization, S.A.M. erases RAM contents and fills it with 16-bit hex values of 0x0000. Then, ROM 1  is copied into RAM.
From there, the program is initialized with the following adresses storing vectors for code:

* $FFFC - ERR
* $FFFD - IRQ
* $FFFE - NMI
* $FFFF - Program Start

Once the initial vectors are loaded into a read-only cache for the CPU to refer to whenever an IRQ, NMI, or ERR interrupt is raised, the CPU jumps to the defined address stored in the Program Start address ($FFFF).

From there, instructions are executed in order. All instructions are single-cycle, mainly due to the design of the emulator.
