
SYNOPSIS
-----
The create-prog.c program will create a program in the input format expected by the simple-mips-simulator consisting of 1024 instruction words assumed to begin at address 0x400000 and 1024 data words at address 0x10000000.

BUILD
-----
Just compile it: `gcc -o create-prog create-prog.c`.

RUN
-----
The program expects three inputs given as positional command line arguments:
```./create-prog textsegment.txt datasegment.txt program.sim```

The first input is the name of a plaintext file, e.g., textsegment.txt, containing the text segment in hex, with one instruction word per line of the file. An example text segment file is given in example-text.txt. This file can be easily created by copy-pasting the hex encoding of the MIPS instructions from an assembly converter, for example by copying from the text segment window of QtSPIM, and removing everything except the hex encoding of the instructions themselves, one per line. Also, the first few lines should be replaced with nops (0). Note that the `create-prog` will generate nops for any instructions needed to pad the output program to 1024 instruction words.

The second input is the name of a plaintext file, e.g., datasegment.txt, containing the data segment in hex, with one data word per line of the file. An example data segment is in example-data.txt. This file can also be easily created from an assembly converter, such as the QtSPIM data segment window.  Again, `create-prog` will generate 0 value data words to pad the program to 1024 data words if needed.

The third input is the name of the output program file to generate, e.g., program.sim, which will contain the 4096B text segment and 4096B data segment generated by converting the two input files.

