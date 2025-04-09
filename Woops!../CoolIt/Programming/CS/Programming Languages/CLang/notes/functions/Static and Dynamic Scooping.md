Before studying this lecture we need to know about [[Memory Layout Of C Program]] so you can check it from the previous link.

In this particular presentation we will focus on [[Stack]] segment.
in order to understand static and dynamic scooping we need to understand this particular segment.

**Applications :**
- Stack is a Container (Or memory segment) which holds some data.
- Data is retrieved in **L**ast **I**n **F**irst **O**ut (**[[LIFO]]**) fashion.
- Two operations which we can perform on Stack : **Push** and **Pop**.
> **PUSH** : simply mean you are pleasing the element on the stack
> **POP** : means you are retrieving the element out of the stack

**How it works :**
- Whenever we are calling a function it will store inside that stack, and this pointer that stored simply means that now this particular function is under the execution. so compiler know that this particular function is under execution.
- Now suppose after make executing some lines of code compiler and counters a call to an another function, so the control will transfer to that function.
- so the control transfer from main function to another function inside it and so on ..
- so suppose after executing some lines of code it encounter a **return** statement..
- **return** simply mean that this function is now over and we should go back the position that we left off.
- when compiler encounter the **return** statement will **Pop** the function out of the stack and will come back to the point where it previously left off until it reach the main function from the beginning.

*this is for the seek of simplicity*

**But what really happens??**

For the seek of simplicity we told that whenever that function is called it will get stored inside the Call Stack. 

But in reality it is not the function what get stored inside the Call Stack it is the **Activation Record** of the function which is maintained inside the call stack.

**What is an Activation Record??**

*Activation Record -* is a portion of a stack which is generally composed of :
- Local of the callee..
> all the local variables of the function.
- Return address to the caller..
> which call the function that can compiler knows where it has to return after the completion of the function.
- Parameter of the callee..
> parameters of the function.

##### So why scooping is important?

Scooping is necessary if you want to reuse variable names.
```C
int fun1() {
	int a = 10;
}

int fun2() {
	int a = 20;
}
```
*In this case the declaration is working.*


##### What is STATIC Scooping ?
*In static scooping (Or lexical scooping)*, definition of a variable is resolved by searching its containing block or function, if that fails, then searching the outer containing block and so on.

```C
int a = 10, int b = 20;
int fun() {
	int a = 5;
	{
		int c;
		c = b/a; // output: 4 but why??
		printf("%d", c);
	}
}
```
As we see the output is *4* but what that actually mean ?
- as *C* that we assign to contain the values of a variable *a* and *b* but there is no *a* and *b* in this local scooping area.
- so it will search for the outer containing block and it find a variable *a* in the nearer outer one.
- so it contain it in *a* one, now it will search for *b*, therefore it is not in the same block the taken *a*.
- so it will search the outer block to find if there is really assigned *b* to contain, and it does so the value of *C* will be *c = 5 / 20* to be *4*.

> As we see it search for the nearer variable to the existing block.


##### the concept of static scooping
If you want to see the [[Memory Layout Of C Program]] to visualize your understanding the concepts, then check the previous link.

In our program we will use these two memory segments *STACK* and *DATA (initialized)* segments.

>the reason of using the *initialized data* segment is that in our program we have *[[global variables]]*, and the global variables find there place in initialized data segment.





##### What is DYNAMIC Scooping?
*In Dynamic scooping*, definition of a variables is resolved by searching its containing block and if not found, then searching its calling function and if still not found then the which called that calling function will be searched and so on.




Check [[Dynamic Scooping HWP]]. 
> To Understand How really Static and Dynamic scooping work.


#### **Important Takeaways..**
- In most of the programming languages, static scooping is followed instead of dynamic scooping.
- Languages, including **[[Algol]]**, **[[Pascal]]**, **[[C]]**, **[[Haskell]]**, **[[Scheme]]** etc. are statically scooped.
- Some languages, including **[[SNOBOL]]**, **[[APL]]**, **[[Lisp]]**, etc. are dynamically scooped.
- As **C** follows static scooping therefore it is not possible to see programmatically, how dynamic scooping works in **C**.

**[[Perl]]** *is a programming language which is supports both static as well as dynamic scoping.*





#function 

