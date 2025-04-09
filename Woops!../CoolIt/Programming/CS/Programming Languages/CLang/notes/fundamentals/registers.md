- First of all before talk about anything in registers in C we need to know the [[Memory hierarchy]] which means:

![[Memory-Hierarchy-Design.webp]]
**Note -** so based on what we see we will conclude that the **Magnetic Tape** has the largest space in memory BUT is also takes longer time to access the memory.

So in contrast, the **CPU Register** memory has the smallest space in memory But it also takes faster time to access the memory. and so on..

*we will not talk about the real memory hierarchy but registers, so if you want to know about the the hierarchy of memory you can check it from the [[Memory hierarchy]] note.*

##### Register Syntax:
```C
#include <stdio.h>

itn main() {
	register int var;  //register some_data_type some_variable_name;
	return 0;
}
```

##### So what is REGISTER modifier?
 *register keyword hints the compiler to store a variable in register memory.*

- This is done because access time reduces greatly for most frequent referred variable.
- This is the **choice of compiler** to whether it puts the given variable in register or not.
- So usually compiler themselves do the necessary optimization.


#VariableModefiers
