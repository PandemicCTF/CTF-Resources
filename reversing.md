# Reversing

## Common utilities assumed to be installed
* [pwntools](http://pwntools.com)
* [radare2](https://rada.re/r/)

## Basic binary analysis (identify ELF and protections)

This would identify the binary along with the common protections, entrypoints
and also import symbols and strings on the data section.

`rabin2 -Iiez mybin`

## Reversing
* [pwndbg](http://foremost.sourceforge.net/) or [gef](https://github.com/hugsy/gef) are two cool gdb based tools
* [radare2](https://rada.re/r/)
* [Hopper](https://www.hopperapp.com/) Good for decompiling to C
* IDA - Best decompiler an power tool overall

## Other cool tools worh knowing
* [pintool](https://github.com/wagiro/pintool) This tries to bruteforce the password char by char based on the number of
  instructions executed on each step.
* [demovfuscator](https://github.com/kirschju/demovfuscator) Counter to [movfuscator](https://github.com/xoreaxeaxeax/movfuscator)
