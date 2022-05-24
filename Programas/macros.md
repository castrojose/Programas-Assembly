
asm
@ simple program setting up a modulus macro

.section    .data
x:
    .long   2013
y:
    .long   19

.macro mod a, b
mod_\@:   cmp \a, \b
            subge \a, \a, \b
            bge mod_\@
.endm

.globl _start

_start:
    ldr r2, =x
    ldr r0, [r2]
    ldr r2, =y
    ldr r1, [r2]
    mod r0, r1

    mov r7, $1
    swi 0
.end 



