
### it has  cool operators 
-  **&** This is called [[AND]] operator
-  **|** This is called [[OR]] operator
- **~** And this is [[NOT]] operator 
- **<<** This is [[Left Shift]] operator
- **>>** And [[Right Shift]] operator
- **^** Finally [[XOR]] operator


### About & operator
- It takes two bites at a time and perform [[AND]] operation.
- AND (&) is binary operator, it takes two numbers and perform bitwise AND.
- Result of AND is 1 when both bites are 1.

#### Example for the operation of AND
![[and-operation.png]]



### About | operator 
- It takes two bites at a time and perform [[OR]] operation.
- OR (|) is binary operator, it takes two numbers and perform bitwise OR.
- Result of OR is 0 when both bites are 0.
-
#### Example for the operation of OR
![[or-operation.png]]



### About NOT (~) operator
- Not is a unary operator .
- It's job to complement each bit one by one.
- Result of NOT is 0 when bit is 1 and 1 when bit is 0.
#### Example for the operation of NOT

| A | ~A |
| ------- |------|
| 1       | 0    |
| 0       | 1    |


### About Left Shift (<<) operator 
#### It may looks like that

    First operand      <<          Second operand 
     ↓                                            ↓
    whose bites get                Decides the number of
     left shifted                places to shift the bites

#### notes
- When bites are shifted left then **trailing** position are filled with zero.
```C
#include <stdio.h>

int main() {
	char var = 3; //Note: 3 in binary = 0000 0011;
	printf("%d", var<<1);
	return0;
}
```

#### how Left shift works?

		var << 1 // left shift by 1 position
**It means**`
```
	if var = 3 // that has this binary number 0000 0011
               // it will shift left to be 0000 011_
               // and the shifted number will be 0 to become 0000 0110 = 6
               // so it will become from 3 to 6.
```

**Important Points
- Left shifting is equivalent to **multiplication** by **2^rightoperand

**Example 

```
we talked before about: 
		if var = 3;
		var << 1      // output: 6 [3 * 2^1]

so if:
		var << 4      // then the output will be: 48 Cuz [3 * 2^4]
```


### About Right Shift (>>) operator 
- It looks like the Left Shift operator from structure point.

#### Notes
- When bites are shifted right then **leading** positions are filled zeros.
```C
#include <stdio.h>

int main() {
	char var = 3; //Note: 3 in binary = 0000 0011;
	printf("%d", var>>1);
	return0;
}
```

#### how right shift works?
```
Now: var >> 1
			var = 3;
			3 = 0000 0011

			it will be: _000 0001
			and the leading positoin will filled with zero to be // 0000 0001

			so the final output will be = 1 instead of 3.
```

**Important Points**
- Right Shifting is equivalent to **division** by **2**^rightoperan
```
So it looks like that:
		if var = 3;
		then var >> 1   // output will be 1 Cuz [3 / 2^1]

		so if var = 32;
		and var >> 4    //output will be 2 Cuz [32 / 2^4]
```


### About XOR (^) operator
- we will show a compare between the [[Inclusive OR]] and the [[Exclusive OR]].

**An Inclusive OR**
- Either A is 1 or B is 1 or Both are 1, then the output is 1.
- Including Both

| A   | B   | A OR B |
| --- | --- | ------ |
| 0   | 0   | 0      |
| 0   | 1   | 1      |
| 1   | 0   | 1      |
| 1   | 1   | 1      |

**An Exclusive OR 
- Either A is 1 or B is 1 then the output is 1 but when Both A and B are 1 then output is 0.
- Excluding Both

| A   | B   | A XOR B |
| --- | --- | ------- |
| 0   | 0   | 0       |
| 0   | 1   | 1       |
| 1   | 0   | 1       |
| 1   | 1   | 0       |

#### Example for the operation of XOR 
![[xor-operation.png]]


#operators

