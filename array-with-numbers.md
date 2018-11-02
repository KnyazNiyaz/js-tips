## Why the map function does not work with some arrays in javascript and what to do with this.


For a clearer demonstration, suppose you need to generate an array of numbers from 0 to 99

const arr = []; 
for (let i = 0; i < 100; i++) { 
  arr[i] = i; 
}

Perhaps the for loop in javascript makes you feel uncomfortable. In fact, many programmers have not used ```for```-cycles for years due to the functions ```forEach()```, ```map()```, ```filter()```, and ```reduce()```.

#### Let’s create with another way! 

```sh
const arr = Array(100);
```

now we have an array of length 100

```sh
const arr = Array(100).map((_, i) => i); 
console.log(arr[0] === undefined); // true
```

### Explanation

When we create an array using constructor functions, you get an array object whose length parameter is equal to what you specified, but there is nothing more in the object.

```sh
['a', 'b', 'c']

	 ||
	 ||
	\  /
	 \/
     
{ 
  0: 'a', 
  1: 'b', 
  2: 'c', 
  length: 3 
}

```
but when we create with the first way, we get only the length
```sh
{ 
  // no indexes! 
  length: 100 
}
```

Solution: 

```sh
const arr = [...Array(100)].map((_, i) => i);
``` 

This is because the destructuring operator is simpler than the map() function

