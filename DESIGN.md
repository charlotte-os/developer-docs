# Master Design File For CharlotteOS

## General Design Points

- Hybrid kernel
- Paravirtualized interfaces to all hardware devices
- Use various compatibility mechanisms for porting software (POSIX, WASM/WASI, JVM, .Net CLR, etc.)
- Focus on ease of use, ease of development, and ease of hacking on the OS itself
- MPL 2.0 License
- Include features that users actually care about
- Create a good looking and well optimized native Rust UI
- Create a modern and easy to use text shell (possibly without Unix like shell scripting)
- Encourage the use of languages like Python instead of shell scripting for portability

## Technical Designs (To Be Formalized in RFCs)

### Access Control

- Use access control lists (ACLs)
- Each ACL is a process specific and contains entries composed of a handle (i.e. process local ID), a type, a permission set, and an index into a global system object table for that type
- Each system object table contains descriptors for the type of system objects it represents as well as the number of processes with access to each (i.e. a reference count)
- Both ACLs and system object tables should be implemented using efficient data structures such as B-Tree Maps or Hash Tables.

### Physical Memory Manager

- Tracks used and unused page frames
- Tracks number of page frames that may be needed but have not yet been allocated
- Uses a hybrid bitmap and queue allocator
	- The bitmap is used as normal to track available and unavailable frames
	- The queue is implemented using a static array and functions as a cache of sorts containing a list of available frames for faster allocation
		- frames in the queue are considered to already have been allocated in the bitmap
		- When frames are returned to the allocator as many possible are pushed to the back of the queue while the rest are marked available in the bitmap
	- Contiguous allocations are possible through the use of the bitmap though they would take longer due to the need to find n contiguous available frames.
		-This lookup can be made faster through the use of AVX2 or AVX-512 instructions to compare large numbers of bits at a time when needed.
