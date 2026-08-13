knew most of the stuff here already from 357 and my own work. good review though. well-wr itten explanations

floating point numbers do not wrap around like integers do. just Nan or inf

replacing multiplication with shifts, adds, and subtracts is pretty cool

~x+1 is the same as negating everything to the left of the rightmost 1

unsigned and twos complement addition and multiplication are the same. result of overflow is equivalent to the binary addition and then truncation of leading bits larger than w

sign extension preserves the value of twos complement numbers. kinda non intuitive. ie storing 1011 (-5) in 8 bits as 11111011 (also -5)

type conversion cares about size first then signedness. ie (unsigned) short is actually short -> int (to get to 32 bits) -> unsigned


some cool stuff about C
firstly remembering a lot of stuff from my syseng exercises, it's funny how author says in_place_swap for two pointers is not actually useful but rather for intellectual amusement (ptr y,x,y = ptr y ^ ptr x)

printf("x = %" PRId32 ", y = %" PRIu64 "\n", x, y); uses macros to generate the correct format strings for fixed width data types. this tells the compiler to read off the correct number of bytes per machine because the fixed width types are typedefs over actual types like long or int, which are system dependent for number of bytes. so these macros map the typedef types to how many of their underlying base type to read off. i doubt i will ever use this knowledge but it's cool to know