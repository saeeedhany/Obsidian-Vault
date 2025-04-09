```C
int func(int num) {
	int count = 0;
	while(num) {
		count++;
		num >>= 1;
	}
	return(count);
}
```

*here is the solution..*
```
110110011 --> 435 // we need to left shift it >> by one until to be ZERO
011011001 --> 227
001101100 --> 108
000110110 --> 54
000011011 --> 27
000001101 --> 13
000000110 --> 6
000000011 --> 3
000000001 --> 1
000000000 --> 0 // so the ZERO will acheve after 9 steps so the ouput willbe //9
```



