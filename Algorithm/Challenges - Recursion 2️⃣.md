## 🍋 Challenges - Recursion 2️⃣

### Example : `reverse`

#### **Question**

문자열을 매개변수로 요구하는 재귀 함수를 작성한다.

이 함수는 인자로 들어온 문자열을 반대로 출력한다.

```js
reverse('awesome'); // emosewa
reverse('rithmschool'); // loohcsmhtir
```

#### **My solution**

```js
function reverse(string) {
  if (string.length === 1) return string[0];

  return string[string.length - 1] + reverse(string.slice(0, -1));
}
```

#### **Reference solution**

```js
function reverse(str){
	if(str.length <= 1) return str;
	return reverse(str.slice(1)) + str[0];
}
```

### Example : `isPalindrome`

#### **Question**

문자열을 매개변수로 요구하고 이 문자열이 팰린드롬인지 여부를 확인하는 재귀 함수를 작성한다.

팰린드롬은 시작 방향과 관계없이 똑같이 읽히는 문자열을 뜻한다.

```js
isPalindrome('awesome'); // false
isPalindrome('foobar'); // false
isPalindrome('tacocat'); // true
isPalindrome('amanaplanacanalpanama'); // true
isPalindrome('amanaplanacanalpandemonium'); // false
```

#### **My solution**

```js
function isPalindrome(string) {
  function reverseString(string) {
    if (string.length === 1) return string[0];

    return string[string.length - 1] + reverseString(string.slice(0, -1));
  }

  return string === reverseString(string);
}
```

#### **Reference solution**

```js
function isPalindrome(str){
    if(str.length === 1) return true;
    if(str.length === 2) return str[0] === str[1];
    if(str[0] === str.slice(-1)) return isPalindrome(str.slice(1,-1))
    return false;
}
```

### Example : `someRecursive`

#### **Question**

배열과 콜백함수를 매개변수로 요구하는 재귀 함수를 작성한다.

이 함수는 배열의 단일 요소가 콜백함수를 만족하는 경우 `true`를 반환한다.

```js
someRecursive([1, 2, 3, 4], isOdd); // true
someRecursive([4, 6, 8, 9], isOdd); // true
someRecursive([4, 6, 8], isOdd); // false
someRecursive([4, 6, 8], val => val > 10); // false
```

#### **My solution**

```js
function someRecursive(nums, callback) {
  if (nums.length < 1) return false;
  if (callback(nums[0])) return true;

  return someRecursive(nums.slice(1), callback);
}
```

#### **Reference solution**

```js
function someRecursive(array, callback) {
    if (array.length === 0) return false;
    if (callback(array[0])) return true;
    return someRecursive(array.slice(1),callback);
}
```

### Example : `flatten`

#### **Question**

다차원 배열을 매개변수로 요구하는 재귀 함수를 작성한다.

이 함수는 배열의 모든 요소를 1차원으로 평탄화한 배열을 반환한다.

```js
flatten([1, 2, 3, [4, 5]]); // [1, 2, 3, 4, 5]
flatten([1, [2, [3, 4], [[5]]]]); // [1, 2, 3, 4, 5]
flatten([[1], [2], [3]]); // [1, 2, 3]
flatten([[[[1], [[[2]]], [[[[[[[3]]]]]]]]]]); // [1, 2, 3]
```

#### **My solution**

```js
function flatten(arr) {
  if (arr.length === 0) return [];

  if (Array.isArray(arr[0])) {
    return flatten([...arr[0], ...arr.slice(1)]);
  }

  return [arr[0]].concat(flatten(arr.slice(1)));
}
```

#### **Reference solution**

```js
function flatten(oldArr){
  var newArr = []
  	for(var i = 0; i < oldArr.length; i++){
    	if(Array.isArray(oldArr[i])){
      		newArr = newArr.concat(flatten(oldArr[i]))
    	} else {
      		newArr.push(oldArr[i])
    	}
  } 
  return newArr;
}
```

> #### 🐰 RÉFÉRENCE
> [JavaScript Algorithms and Data Structures Masterclass](https://www.udemy.com/course/js-algorithms-and-data-structures-masterclass/ "JavaScript Algorithms and Data Structures Masterclass")
