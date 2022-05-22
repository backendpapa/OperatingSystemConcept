# Process Concept

```
A process is a program in execution.
```

A process layout or architecture is divided into several sections. They are

1. Text Section - Layer contains executable codes
2. Data Section - Layer contains global variable
3. Heap Section - Dynamically allocated memory during program runtime
4. Stack Section - Temporar data storage when invoking functions such as variables, function parameters and addresses.


- Text and Data section are fixed and do not grow, but the Heap and Stack grow or shrink dynamically
- When a function is called, the ```activation record``` containing the funcion parameter, local variable and address are pushed to the stack.
- The stack increases in size and more heap are allocated.
- Once execution is completed and the function returns control, the Heap and the Stack shrinks back.


```
    A program is a passive entity, it becomes a process when it loaded into memory and thereby turns to a passive entity
```

```js
#include <stdio.h>
#include <stdlib.h>

int x;
int y = 15;

int main(int argc, char * argv[]){
    int *values;
    int i;
    
    
    values = (int *)malloc(sizeof (int)*5);
    
    for(i = 0; i < 5;i++){
        values[i]=i;
        return 0;
    }
}
```


## Process State

A process have a state that defines its current activity. They are:

1. New - when a process is being created
2. Ready - Its waiting to be assigned a processor
3. Running - Process's instructions are being executed
4. Waiting - Process is waiting for an event to occur such as I/O before continuing execution
5. Terminated - Process have finished execution.

