# Lec_3-7

## Compiling a Program
- Source file is first preprocessed
    + `gcc -E` to see output
- Preprocessed file is then compiled to assembly
    + Scanner
    + Type checker
    + Code generator
    + Optimizer
- Assembler converts assembly code to object code
- Object files are converted into an executable

## Dynamically Allocated Memory
- Unlike the stack, the heap grows upwards, and tends not to shrink
- Variables in the heap remain until deallocated 
- Useful for unknown sizes until compile time
- User Managed Heap vs. Garbage Collection 
    + Garbage Collection
        * Do not have to keep track of objects
        * Slows down execution, collection is expensive
    + User Managed Heap
        * Can control what time to deallocate memory
        * More error-prone because you have to keep track of everything

### Memory Management Functions
- `void *malloc(size_t amount)`
    + Allocates amount of bytes in memory from heap and returns a pointer to the beginning of it
    + No initialization of the space
- `void *calloc(size_t count, size_t object_size)`
    + Allocates *count* objects of size *object_size* and returns a pointer to the beginning of it
    + Initializes all the space to 0
- Both return NULL if the allocation fails (no memory available)
- In `<stdlib.h>`
- `free(void *ptr)`
    + Deallocates the memory where *ptr* is pointing to
    + *ptr* can be reused for allocation after this
    + This does not change where ptr is pointing to, just deallocates the space

