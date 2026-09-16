3.1 is background, 3.2 is about assembly and machine level code. each line in an assembly file is one instruction, which gets translated into a sequence of hex codes 

3.3 is data formats and what letter is used to abbreviate each size

3.4 is about move class of instructions, to and from registers, immediate values, and memory locations. talks about what to do when moving stuff of one size to a location of larger size, as well as moving on and off the stack. stack addresses start high and grow lower, heap addresses start low and grow upward so they can take up as much space as they need and is available. stack pointer is kept in one specific register %rsp

3.5 is about arithmetic and logic operations instruction classes. load effective address (leaq) does not actually dereference memory at all, it just copies the effective address to the destination (stores the address as a number, not the value at that address. compilers use it to do some cool gimmicks using the address generation unit (AGU) instead of arithmetic and logic unit (ALU) with calculations of the form Base + Scale × Index + Offset. jeez this stuff is deep man. super deep. 
- leaq
- binary operators ie. %rax,%rdx subtract %rax from %rdx
- unary operators ie. incq (%rsp) to increment stack ptr
- shift operations 
didn't like this section very much

3.6 is about control. jump instruction alters the execution order of machine code. cpu has a set of single-bit condition registers, changed using the SET class of instructions. goto statement from c++ mirrors how assembly code uses jumps. didn't know about goto, it's considered bad practice though. 

implementing control using **conditional moves** is also very cool because it affects processor pipelining and avoids refilling the pipeline from a missed prediction. comparative move is only one instruction (if x then y = z), so you can transfer data instead of control. good when computing both results is cheap i guess. and both have to be possible as well. expected cost of branching = misprediction_probability × misprediction_penalty, compare this with cost of computing both results. **learning to profile must be important to know when one or the other is better**

**guarded-do** implementation of loops as opposed to jump to middle is a little weird but allows optimization of the loop condition because there is only one path to the test expression, which is through the body. so if body established something that makes the condition never true, compiler can delete the loop, or skip the condition if it will always be true. optimizer decides when to use this

switch statements are good because they use a **jump table**, which is efficient and used with **indirect jump instruction** when there are dense set of possibilities in a small range

3.7 is procedures. procedures need control passing, data passing, and memory management. there 6 registers for passing integer/ptr arguments, and 8 for floating point (on linux and mac). **call** instruction passes control, registers and then stack frame are used to pass data following certain conventions. mutual recursion sounds freaky but just follows the same stack patterns

3.8 is array allocation and access. cool that ptr subtraction returns number of elements ie. difference in bytes / sizeof(type), just like addition automatically uses sizeof(type).

stopped at 3.8.3








