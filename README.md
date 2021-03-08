# Hi, I'm S.A.M.! S.A.M. I am!

S.A.M is short for Scratch Advanced Microcomputer.
S.A.M is a fully custom 16-bit simulator written using Scratch 3.0.

# Simulator features
 * It has a built-in MOS 6502-style assembler.
 * It has a AIOC (Advanced I/O Controller) built-in to interface with external Scratch code.
 * 2 64 KiB Memory spaces w/ programmable bank switching
 * 16-bit RAM/ROM

# CPU Features
 * All instructions are big endian format.
 * Simple instruction format.
 * Variable-length instructions.
 * Modified Von-Neuman architecture to easily access the bank-switchable 64 KiB RAM/ROM space.

# How does S.A.M. work?

## THE BARE BONES
Starting with initialization, S.A.M. erases RAM contents and fills it with 16-bit hex values of 0x0000. Then, ROM 1  is copied into RAM.
From there, the program is initialized with the following adresses storing vectors for code:

* $FFFC - ERR
* $FFFD - IRQ
* $FFFE - NMI
* $FFFF - Program Start

Once the initial vectors are loaded into a read-only cache for the CPU to refer to whenever an IRQ, NMI, or ERR interrupt is raised, the CPU jumps to the defined address stored in the Program Start address ($FFFF).

From there, instructions are executed in order. All instructions are single-cycle, mainly due to the design of the simulator.

## WRITING SOFTWARE
Developing software for S.A.M. is simple. You can choose between 3 avaiable options:

### 1. SBA (Scratch Block-Based Assembly)
Using a custom editor, SBA is a Scratch-like programming language developed using Scratch 3.0 itself! It's simple visual-based, drag-and-drop style programming is ideal for starting out with programming S.A.M. You can compile SBA code to S.A.M. Assembly as well as S.A.M. Machine Code, but not backwards.

### 2. Ol' Fashioned 6502-Style Assembly
The MOS 6502 is arguably one of the most infuential CPUs ever made (as for example: The Commodore 64 and/or Apple II). S.A.M. can be programmed using very similar syntax. The built-in assembler uses syntax similar to the Ben Eater 6502 Programming series on Youtube. Please take a look at Ben's series first. Simply replace the OpCodes or your instructions and you'll be up and running in no time!

### 3. Pure Machine Code
If you fancy it, S.A.M. supports pure machine code as well! Please take a look at the documentation for OpCode references as well as more in-depth details about the inner workings of S.A.M. It's also a wise idea to backup your ROM code into a text file in the event of the RAM/ROM resetting.
