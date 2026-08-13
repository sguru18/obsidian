3.1 is background, 3.2 is about assembly and machine level code. each line in an assembly file is one instruction, which gets translated into a sequence of hex codes 

3.3 is data formats and what letter is used to abbreviate each size

3.4 is about move class of instructions, to and from registers, immediate values, and memory locations. talks about what to do when moving stuff of one size to a location of larger size, as well as moving on and off the stack. stack addresses start high and grow lower, heap addresses start low and grow upward so they can take up as much space as they need and is available. stack pointer is kept in one specific register %rsp

3.5 is about arithmetic and logic operations instruction classes. load effective address (leaq) does something funky that does not actually reference memory at all, it copies the effective address to the destination (stores the computed address, not the value at that address. compilers use it to do some cool gimmicks using the address generation unit (AGU) instead of arithmetic and logic unit (ALU) with calculations of the form Base + Scale × Index + Offset. jeez this stuff is deep man. super deep. 
- leaq
- binary operators ie. %rax,%rdx subtract %rax from %rdx
- unary operators ie. incq (%rsp) to increment stack ptr
- shift operations 
didn't like this section very much

3.6 is about control. jump instruction alters the execution order of machine code. cpu has a set of single-bit condition registers, changed using the SET class of instructions. 





