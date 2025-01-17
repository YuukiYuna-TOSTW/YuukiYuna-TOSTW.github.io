---
title: Star Pattern Code
date: 2025-01-15
categories: Project
categories: Study
tags: [Assembly 8086, Compiler 8086]     # TAG names should always be lowercase
image:
    path: assets/📚☆﹒ faruzan birthday art 2023 !!.jpg
---

# My Star Pattern Project Code
Hello everyone, I'm Aristo from Ciputra Makassar University. In this side I will show you all about my star pattern program. This program will run with Assemly 8086 leaguange. The result of this program is a Star Pattern with right triangle shape. The program will use star simbol to make the shape. Next I will show all of you the rest of the coding that I made.

```

SET 0
star: DB 0x2A

start:
MOV AX, 0
MOV DS, AX
MOV SI, OFFSET star
MOV AH, 0x13
MOV BL, 6

_loop:
INC CX
INC CX
INT 0x10
MOV AL, byte DS[SI]
INC DI
INC DI
MOV byte DS[DI], AL
CMP CL, BL
JNE _loop
HLT
```