## 🍋 Challenges - Recursion

### Example : `power`

#### **Question**

밑과 지수를 매개변수로 요구하는 함수를 작성한다.

밑의 지수에 해당하는 거듭제곱을 반환해야하며 `Math.pow()`는 사용이 금지된다. (같은 기능을 수행해야 한다.)

```js
power(2, 0); // 1
power(2, 2); // 4
power(2, 4); // 16
```

#### **My solution**

```js
function power(base, exponent) {
  if (exponent === 0) return 1;

  return base * power(base, exponent - 1);
}
```

#### **Reference solution**

```js
function power(base, exponent){
    if(exponent === 0) return 1;
    return base * power(base,exponent-1);
}
```

### Example : `factorial`

#### **Question**

숫자를 매개변수로 요구하고 해당 숫자의 팩토리얼을 반환하는 함수를 작성한다.

팩토리얼은 해당 숫자부터 1까지 전부 곱하는 것을 말하며, 0!은 항상 1이다.

```js
factorial(1); // 1
factorial(2); // 2
factorial(4); // 24
factorial(7); // 5040
```

#### **My solution**

```js
function factorial(num) {
  if (num === 0 || num === 1) return 1;

  return num * factorial(num - 1);
}
```

#### **Reference solution**

```js
function factorial(x){
   if (x < 0 ) return 0;
   if (x <= 1 ) return 1;
   return x * factorial(x-1);
}
```

### Example : `productOfArray`

#### **Question**

숫자를 요소로 가진 배열을 매개변수로 요구하는 함수를 작성한다.

배열 내의 모든 숫자의 곱을 반환한다.

```js
productOfArray([1, 2, 3]); // 6
productOfArray([1, 2, 3, 10]); // 60
```

#### **My solution**

```js
function productOfArray(nums) {
  if (nums.length === 1) return nums[0];

  return nums.pop() * productOfArray(nums);
}
```

#### **Reference solution**

```js
function productOfArray(arr) {
    if(arr.length === 0) {
        return 1;
    }
    return arr[0] * productOfArray(arr.slice(1));
}
```

### Example : `recursiveRange`

#### **Question**

숫자를 매개변수로 요구하는 함수를 작성한다.

이 함수는 인자로 들어온 숫자부터 0까지의 합을 반환한다.

```js
recursiveRange(6); // 21
recursiveRange(10); // 55
```

#### **My solution**

```js
function recursiveRange(num) {
  if (num === 0 || num === 1) return num;

  return num + recursiveRange(num - 1);
}
```

#### **Reference solution**

```js
function recursiveRange(x){
   if (x === 0 ) return 0;
   return x + recursiveRange(x-1);
}
```

### Example : `fib`

#### **Question**

숫자를 매개변수로 요구하고 피보나치 수열에서 해당 숫자번 째 수를 반환하는 재귀 함수를 작성한다.

피보나치 수열은 1, 1로 시작하는 수열로 이후의 숫자는 앞의 두 숫자의 합과 같다. (`1, 1, 2, 3, 5, 8, ...`)

```js
fib(4); // 3
fib(10); // 55
fib(28); // 317811
fib(35); // 9227465
```

#### **My solution**

```js
function fib(num) {
  if (num === 1 || num === 2) return 1;

  return fib(num - 1) + fib(num - 2);
}
```

#### **Reference solution**

```js
function fib(n){
    if (n <= 2) return 1;
    return fib(n-1) + fib(n-2);
}
```

> #### 🐰 RÉFÉRENCE
> [JavaScript Algorithms and Data Structures Masterclass](https://www.udemy.com/course/js-algorithms-and-data-structures-masterclass/ "JavaScript Algorithms and Data Structures Masterclass")
