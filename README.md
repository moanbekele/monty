#  0x19. C - Stacks, Queues - LIFO, FIFO
**Description**
## Data structures:
* Header includes the following data structures. 
```
/**
 * struct stack_s - doubly linked list representation of a stack (or queue)
 * @n: integer
 * @prev: points to the previous element of the stack (or queue)
 * @next: points to the next element of the stack (or queue)
 *
 * Description: doubly linked list node structure
 * for stack, queues, LIFO, FIFO
 */
typedef struct stack_s
{
        int n;
        struct stack_s *prev;
        struct stack_s *next;
} stack_t;
```
```
/**
 * struct instruction_s - opcode and its function
 * @opcode: the opcode
 * @f: function to handle the opcode
 *
 * Description: opcode and its function
 * for stack, queues, LIFO, FIFO
 */
typedef struct instruction_s
{
        char *opcode;
        void (*f)(stack_t **stack, unsigned int line_number);
} instruction_t;
```



## Compilation & Output
* code will be compiled this way:   ```gcc -Wall -Werror -Wextra -pedantic -std=c89 *.c -o monty```


# **Main Tasks**

  ## 0. push, pall
  - The opcode pall prints all the  values on the stack, starting from the top of the stack.

  - Usage pall
  - Format: see example
  - If the stack is empty, don’t print anything
 ```
julien@ubuntu:~/monty$ cat -e bytecodes/00.m
push 1$
push 2$
push 3$
pall$
julien@ubuntu:~/monty$ ./monty bytecodes/00.m
3
2
1
julien@ubuntu:~/monty$
 ```

  ## 1. pint

  Implement the `pint` opcode.

  > The pint opcode

    - The opcode pint prints the value at the top of the stack, followed by a new line.

    - Usage: pint
    - If the stack is empty, print the error message L<line_number>: can't pint, stack empty, followed by a new line, and exit with the status EXIT_FAILURE

 ```
  julien@ubuntu:~/monty$ cat bytecodes/06.m 
push 1
pint
push 2
pint
push 3
pint
julien@ubuntu:~/monty$ ./monty bytecodes/06.m 
1
2
3
julien@ubuntu:~/monty$ 
 ```
## 2. pop
 - Implement the pop opcode.

  ### The pop opcode

    - The opcode pop removes the top element of the stack.

    - Usage: pop
    -  If the stack is empty, print the error message L<line_number>: can't pop an empty stack, followed by a new line, and exit with the status EXIT_FAILURE
    ```
    julien@ubuntu:~/monty$ cat bytecodes/07.m 
push 1
push 2
push 3
pall
pop
pall
pop
pall
pop
pall
julien@ubuntu:~/monty$ ./monty bytecodes/07.m 
3
2
1
2
1
1
julien@ubuntu:~/monty$ 
    ```

 ## 3. swap

  Implement the swap opcode.

  The swap opcode

  The opcode swap swaps the top two elements of the stack.

    - Usage: swap
    - If the stack contains less than two elements, print the error message L<line_number>: can't swap, stack too short, followed by a new line, and exit with the status EXIT_FAILURE
    ```
    julien@ubuntu:~/monty$ cat bytecodes/09.m 
push 1
push 2
push 3
pall
swap
pall
julien@ubuntu:~/monty$ ./monty bytecodes/09.m 
3
2
1
2
3
1
    julien@ubuntu:~/monty$ 
    ```
 ## 4. add
Implement the add opcode.

  The add opcode

  The opcode add adds the top two elements of the stack.

    - Usage: add
    - If the stack contains less than two elements, print the error message L<line_number>: can't add, stack too short, followed by a new line, and exit with the status EXIT_FAILURE
    - The result is stored in the second top element of the stack, and the top element is removed, so that at the end:
      - The top element of the stack contains the result
      - The stack is one element shorter
      ```
julien@ubuntu:~/monty$ cat bytecodes/12.m 
push 1
push 2
push 3
pall
add
pall
julien@ubuntu:~/monty$ ./monty bytecodes/12.m 
3
2
1
5
1
julien@ubuntu:~/monty$
      ```
##5. nop

  Implement the nop opcode.

  The nop opcode

    - The opcode nop doesn’t do anything.

    - Usage: nop


  


