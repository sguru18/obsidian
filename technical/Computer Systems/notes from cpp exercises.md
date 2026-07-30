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