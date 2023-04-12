## 🍋 Challenges - Frequency Counter

### Example : `sameFrequency`

#### **Question**

양의 정수 2개를 매개변수로 요구하는 함수를 작성한다.

두 숫자의 구성이 같은 빈도수로 발생하는지의 여부를 반환해야 하고 `O(N)`의 시간 복잡도를 가져야만 한다.

```js
sameFrequency(182, 281); // true
sameFrequency(34, 14); // false
sameFrequency(3589578, 5879385); // true
sameFrequency(22, 222); // false
```

#### **My solution**

```js
function sameFrequency(num1, num2) {
  const str1 = num1.toString();
  const str2 = num2.toString();

  if (str1.length !== str2.length) return false;

  const frequency = {};

  for (const str of str1) {
    // 숫자가 존재하면 +1, 없으면 추가
    frequency[str] = (frequency[str] || 0) + 1;
  }

  for (const str of str2) {
    // 숫자가 존재하지 않거나 개수가 0이면 false
    if (!frequency[str]) return false;
    else frequency[str] -= 1;
  }
  return true;
}
```

#### **Reference solution**

```js
function sameFrequency(num1, num2) {
  let strNum1 = num1.toString();
  let strNum2 = num2.toString();
  if (strNum1.length !== strNum2.length) return false;

  let countNum1 = {};
  let countNum2 = {};

  for (let i = 0; i < strNum1.length; i++) {
    countNum1[strNum1[i]] = (countNum1[strNum1[i]] || 0) + 1;
  }

  for (let j = 0; j < strNum1.length; j++) {
    countNum2[strNum2[j]] = (countNum2[strNum2[j]] || 0) + 1;
  }

  for (let key in countNum1) {
    if (countNum1[key] !== countNum2[key]) return false;
  }

  return true;
}
```

### Example : `areThereDuplicate`

#### **Question**

다양한 요소를 매개변수로 받아들이는 함수를 작성한다.

인자에 중복되는 요소가 있는지 여부를 반환해야 한다.

Frequency Counter 패턴 또는 Multiple Pointers 패턴으로 문제를 풀 수 있다.

```js
areThereDuplicate(1, 2, 3); // false
areThereDuplicate(1, 2, 2); // true
areThereDuplicate('a', 'b', 'c', 'a'); // true
```

#### **My solution**

```js
// Frequency Counter 패턴
function areThereDuplicates(...args) {
  if (args.length === 0 || args.length === 1) return false;

  const frequency = {};

  // args 요소가 객체에 없으면 추가, 있으면 +1
  for (const el of args) {
    frequency[el] = (frequency[el] || 0) + 1;
  }

  // 객체 중 값이 1보다 큰 것이 존재하면 true
  for (const el in frequency) {
    if (frequency[el] > 1) return true;
  }
  return false;
}
```

#### **Reference solution**

```js
// Frequency Counter 패턴
function areThereDuplicates() {
  let collection = {}
  for(let val in arguments){
    collection[arguments[val]] = (collection[arguments[val]] || 0) + 1
  }
  for(let key in collection){
    if(collection[key] > 1) return true
  }
  return false;
}
```

> #### 🐰 RÉFÉRENCE
> [JavaScript Algorithms and Data Structures Masterclass](https://www.udemy.com/course/js-algorithms-and-data-structures-masterclass/ "JavaScript Algorithms and Data Structures Masterclass")
