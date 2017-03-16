# Lecture 3-9

## Dynamic Memory Allocation
```c
/* max num of characters in a name */
#define MAX_LEN 20

typedef struct Student {
   char *name;
   int age;
} Student;

int main() {
    Student *student;

    /* allocates memory in heap for a student */
    student = malloc(sizeof(Student)); 
    if (student == NULL) {
        exit(EXIT_FAILURE);
    }

    /* allocates a separate space in heap for the name */
    student->name = malloc(sizeof(char) * MAX_LEN); 

    /* implementation */

    /* frees the pointers, that is deallocating space */
    free(student); 
    free(student->name);
    return EXIT_SUCCESS
}
```

- `free(NULL)` is a valid statement
- If you have pointer `p` that points to a space in memory, you can't do things like `p++; free(p)` -> gives error

## Function Pointers

- If you have function: 

```c
void function(int x) {
    printf("Hello%d\n", x);
}

void use_function(void (*some_name)(int)) {
    some_name(300); 
}

int main(void) {
    /* normally calling function */
    function(10); 
    /* pointer to my_function */
    void (*func_ptr)(int x);
    func_ptr = function; 

    /* using function using pointer */
    func_ptr(200);  
    return 0;
}
```

- By using a function pointer, you can pass functions as variables to another function
