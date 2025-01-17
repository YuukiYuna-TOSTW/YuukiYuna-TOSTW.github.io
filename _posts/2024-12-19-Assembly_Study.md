---
title: Assembly Study 8086
date: 2024-12-19
categories: Study
tags: [Assembly 8086, Compiler 8086]
image:
    path: assets/b73a7d06-0ceb-460d-92b1-8aea0ed73e23.jpg
---

# My First Assembly 8086

Hello everyone, I'm Aristo from Ciputra Makassar University. In this side I will show you all my first Assembly 8086 study program. When make this program I learn many thing about Assembly 8086 Leaguange. Next I will show all of you the rest of the coding that I made.

# The ADD Assembly 8086 Program

In this program I made an instruction to solve a problem that want us to do summation from number 3 and number 2. When we run the program, the program will set a value for register Al and BL first with number 3 for register Al and number 2 for register BL. After set the value then the program will ADD the value from register BL to register AL to summation the number. To display the output, the program will convert the value inside the DL to ASCII. after convert the value then the program will display the result with the INT 0x21 Instruction. After all the instruction done then the program will stop the running with HLT instruction. Next I will show all of you the rest of the coding that I made.
```
start:
MOV AL, 0x3
MOV BL, 0x2
ADD AL, BL
MOV DL, AL
ADD DL, 0x30
MOV AH, 0x02
INT 0x21
HLT
```
# The SUB Assembly 8086 Program
In this program I made an instruction to solve a problem that want us to do substraction from number 5 and number 3. When we run the program, the program will set a value for register AL and BL first with number 5 for register AL and number 3 for register BL. After set the value then the program will SUB the value from register BL to register AL to substration the number. To display the output, the program will convert the value inside the DL to ASCII. after convert the value then the program will display the result with the INT 0x21 Instruction. After all the instruction done then the program will stop the running with HLT instruction.  Next I will show all of you the rest of the coding that I made.
```
start:
MOV AL, 0x5
MOV BL, 0x3
SUB AL, BL
MOV DL, AL
ADD DL, 0x30
MOV AH, 0x02
INT 0x21
HLT
```