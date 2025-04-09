#### Let us feel it: ? :
**Note -** Conditional operator is a [[Ternary operator]] therefor it requires **THREE** operands.

##### so why we need this Conditional Operator?
```C
char result;
int marks;

if (marks > 33) {
	result = 'p';
}else {
	result = 'F';
}
```
*this is the traditional way to write this condition*

***ternary operator way***
```C
char result;
int marks;

result = (marks > 33) ? 'p' : 'f';
```
*as we see its a hole different between the traditional way and the ternary way.*

#### Quick Facts:
- Conditional operator is the only [[Ternary operator]] available in the list of operators in C language.
- As in *Expression1 ? Expression2 : Expression3*, expression1 is the boolean expression, if simply write 0 instead of some boolean expression than that simply means FALSE and therefore expression3 will get evaluated.

##### example: 
```C
int result;

result = 0 ? 2 : 1;  //the result will be 1 CUZ 0 means FALSE so the third expression will evaluated.
```


#operators 
