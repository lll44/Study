
## 2022-01-28: [Calculate Century Year](https://www.codewars.com/kata/5a3fe3dde1ce0e8ed6000097/train/javascript)

```js
const century = year => Math.ceil(year/100)
```

```js
function century(year) {
  return Math.ceil(year / 100);
}
```

```js
function century(year) { // My solution
  var calcYear = year / 100;
  
  if (year % 100 === 0) {
    return calcYear;
  } else {
      return Math.ceil(calcYear);
  }
}
```


## 2022-01-28: [Calculate Averages](https://www.codewars.com/kata/57a2013acf1fa5bfc4000921/train/javascript)

Write a function which calculates the average of the numbers in a given list.

**Note:** Empty arrays should return 0.

```js
function find_average(array) {
  // your code here
  return 0;
}
```


```js
function find_average(array) {
  if (array.length === 0) {
  return 0;
  }
  var result = 0;
  for (i=0; i<array.length; i++) {
    result +=array[i];
  }
  return result/array.length;
}
```

## 2022-01-27: [Even or Odd](https://www.codewars.com/kata/53da3dbb4a5168369a0000fe/solutions/javascript)

Create a function that takes an integer as an argument and returns "Even" for even numbers or "Odd" for odd numbers.

```
function even_or_odd(number) {
  
}
```


```
function even_or_odd(number) {
  return number % 2 ? "Odd" : "Even"
}
```

```
function even_or_odd(number) {
  if (number%2 == 0) {
    return "Even";
  } else {
    return "Odd";
  }
}
```