summary of [[containers]]

**asm volatile("" : : "r,m"(val) : "memory");**
asm = inline assembly

volatile = telling compiler do not remove even if u want to
this line prevents a compiler from optimizing away a certain value, tells the compiler to move val into a register as if it is being used by something, and assume memory has been read or written to so it can't reorder this to the end or something. useful for benchmarking

**constexpr** is very cool, gives you values and essentially "runs some code" at compile time, putting values directly into the binary's read only memory.

**scopeguard implementation** is really cool, extremely simple but so powerful. used when you don't want a whole class to define the cleanup behavior or when cleanup behavior needs local variable access.

**inline** is useful for extremely tiny functions, compiler just pastes content instead of mov with return result and other overhead.

returning const char * is cheaper for small non-changing strings instead of string

need **noexcept** on move constructors else compiler doesn't trust and just copies. 

&& is pass by **r-value reference**, a reference to a temporary or something passed via std::move(). basically says this object is being moved not copied, you can steal everything from its internals.

**stack unwinding** is when the runtime encounters an exception so it walks back up the call stack to clean up all live objects 

**smart pointers** are nutty and kinda complicated. essence of them is ownership and owner / child lifetime relations. clean relation means unique_ptr is fine. **raw pointers are for borrowing** memory, not owning ie. the borrowed object's lifetime has nothing to do with this object's lifetime
- unique_ptr
	- single owner, non-copyable but movable. delete called automatically when the object pointed to goes out of scope. highly optimal and clean
	- generally use make_unique, only use unique_ptr() constructor when not doing a new allocation, ie. making an existing pointer into a smart one. 
- shared_ptr
	- useful for when there are multiple owners with unclear lifetime (graph nodes with unclear parent) or owner lifetime doesn't match pointer lifetime (background thread or something)
	- likely not useful though because large overhead in incrementing ref counter
- weak_ptr
	- solves the circular reference problem, holds a reference but does not increment the count, useful for observing ie. a cache that doesn't keep something alive just because it has a reference