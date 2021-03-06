# AssemblySharp

- [English](Readme.md)
- [한국어](Readme.ko.md)

Implementation of  C/C++ `__asm` or ` __asm__` keywords as closely as possible in C#.
We use standard Intel syntax used in Microsoft Micro Assembler (MASM) assembler.
Works on .Net framework 4.7

## Usage

```csharp
int a = 200;
int result = (int)X86Assembly.ExecuteScript(
    ASM.MOV, REG.EAX, 100,
    ASM.ADD, REG.EAX, a,
    ASM.RET);
Console.WriteLine(result); // 300

int i = 100;
result = X86Assembly.ExecuteScript(
    ASM.mov, REG.EAX, 0,
    ASM.mov, REG.ECX, i,
    new Label("myloop"),
    ASM.add, REG.EAX, REG.ECX,
    ASM.loop, "myloop",
    ASM.ret));
Console.WriteLine(result); // 5050
```

## Requirements

Should be installed gcc, objdump. You ㅍneed to set your PATH environment variable to include directory of them.

## [X86Sharp](https://github.com/phillyai/X86Sharp)

X86 VM developed in this project but moved to .Net Core 2.0

## [LICENSE](/LICENSE)

The MIT License (MIT) Copyright (c) 2017 phillyai
