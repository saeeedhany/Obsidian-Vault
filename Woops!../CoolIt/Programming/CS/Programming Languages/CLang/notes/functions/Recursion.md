#### **Outline**
- Definition of Recursion.
- program to demonstrate recursion.
- [[Recursion HWP]].

**Definition of recursion?**
*recursion* is a process in which a function calls itself directly or indirectly.
```C
int fun() {
	...
	fun();
}
```
*here the function call itself*


#### **So How to Write a Recursive Program?**

##### **The Idea:**
- divide the problem into smaller sub-problems.
- Specify the base condition to stop the recursion.
> you must have a number to base condition to stop your recursion at it so you will fell into an infinite loop.


**Problem :**
*Calculate the **factorial** of a number*
So what is a factorial of a number?
```
	factorial of 5: 5 * 4 * 3 * 2 * 1 = 120
```

*in most situations there is a **basic structure** to any recursive program :*
```C
Fact() {
	if() {
		...
	}
	else {
		...
	}
}
```
*this is how basic structure in any recursive program looks like.
- It consist of one *If* construct.
- And one *else* construct.

- **If** construct is the place where we add the *Base Case*.
- **else** construct is the place where we add our *recursive procedure*.
> *Recursive procedure* is the first thing you must write, and then you write the *base case*.

*now lets go back to the **idea** that we talk about before*
- Divide the problem into a smaller sub-problems?
```
**Calculate Fact(4)
//first we need to think about an easier way like suppose..
Fact(1) = 1
//Now what is factorial of (2)
Fact(2) = 2 * 1
// now if we obsirve this very curfully then we can replace thes (1) by Fact(1).
//to be like this 
Fact(2) = 2 * Fact(1)
// so what is Fact of 3?
Fact(3) = 3 * 2 * 1 // as the same way it can be = Fact(3) = 3 * Fact(2)
// and so on..
Fact(4) = 4 * Fact(3)
```
*as the same way if we think of **Fact(n) = n * Fact(n-1)***

*So if we want to write in an actual program :* **We have two steps**
*step #1 -* add the recursive procedure.
```C
	Fact(int n) //here we add an interger value as parameter 
	{ 
		if ()
		{
			...
		}
		else
		{
			return n * Fact(n-1); // now we add the recursive procedure.
		}
	}
```
*after adding the recursive procedure there much more in our code*
we just have to specify the *base condition*.

**So what is the base condition?**
*Base Condition* is the one which doesn't require to call the same function again and it helps in stopping the recursion.

In our case we can take the *Fact(1)* or *Fact(2)* as our base case, so the second step will be..
*step #2 -* adding the *Fact(1)* as base case.
```C
Fact(int n) 
	{ 
		if (n == 1) // here we add our condition that will stop the recursion
		{
			return 1; // if the condition is fulfilled it returns 1
		}
		else
		{
			return n * Fact(n-1); 
		}
	}
```

*After we talk about the concept, Now lets execute the real code*
```C
#include <stdio.h>

int fact(int n) {
	if (n == 1) {
		return 1;
	}else {
		return n * fact(n - 1);
	}
}

int main() {
	int n;
	printf("Enter the number :");
	scanf("%d", n);
	printf("your factorial number %d is %d", n, fact(n));
	return 0;
}
```


#### **Types Of Recursion**
- Direct recursion
- Indirect recursion
- Tail recursion 
- Non-tail recursion

*1.* **Direct recursion**
A function is called direct recursive if it calls the same function again.
```C
fun() {
	//some code
	fun();
	//some code
}
```

*2.* **Indirect recursion**
A function (let say *fun*) is called indirect recursive if it calls another function (let say *fun2*) and then *fun2* calls *fun* directly or indirectly. *It seems complicated*
```C
int fun() {
	//some code
	fun2()
}
int fun2() {
	//some code
	fun()
}
```

*A real example of an Indirect recursion :*
```C
void add();
void even();
int n = 1;

void odd() {
	if (n <= 10) {
		printf("%d", n + 1);
		n++;
		even()
	}
	return;
}
void even() {
	if (n <= 10) {
		printf("%d", n - 1);
		n++;
		odd();
	}
	int main() { // output: 2 1 4 3 6 5 8 7 10 9
		odd();
	}
}
```

*3.* **Tail recursion**
A recursive function is said to b *Tail recursive* if the recursive call is the last thing done by the function. there is no need to keep record of the previous state.

*An example*
```C
void fun(int n) {
	if (n == 0) {
		return;
	}else {
		printf("%d", n); // output: 3 2 1
		return fun(n - 1);
	}
}
int main() {
	fun(3);
	return 0;
}
```

*3.* **None-Tail recursion**
A recursive function is said to be *none-tail recursive* if the recursive call is not the last thing done by the function. after returning back, there is something left to evaluate.

*An Example* 
```C
void fun(int n) {
	if (n == 0) {
		return;
	}else {
		fun(n - 1);
		printf("%d", n); // output: 1 2 3
	}
}
int main() {
	fun(3);
	return 0;
}
```

##### **Advantages and Disadvantages**

Which bath should i follow? **Iterative** Or **Recursive**
- Every recursive program can be written as iterative program.
so the natural question is, **Which part should i follow?**

**Advantages**
- Every recursive program van be modeled into an iterative program but recursive program are more elegant and requires relatively less lines of code.
*Iterative*
```C
int fact(int n) {
	int res = 1;
	while (n != 0) {
		res = res*n;
		n--;
	}
	return res;
}
int main() {
	printf("%d", fact(5));
	return 0;
}
```

*Recursive*
```C
int fact(int n) {
	if (n == 1) 
		return 1;
	else 
		return n * fact(n - 1);
}
int main() {
	prntf("%d", fact(5));
	return 0;
}
```

**Disadvantages**
- Recursive programs requires more space that iterative programs.



#function