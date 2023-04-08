## 🍋 Frequency Counter

### Frequency Counter 패턴

`Object`나 `Set`을 이용해 값과 빈도수를 수집하는 패턴이다.

서로 다른 입력값 사이의 포함관계, 애너그램 관계, 빈도수 비교에 유용하다.

### Example : `same`

#### **Question**

두 개의 `number` 배열을 매개변수로 요구하는 함수를 작성한다.

첫 번째 배열의 모든 요소의 제곱이 두 번째 배열의 모든 요소와 일치한다면 `true`를 반환해야한다.

단, 모든 요소의 빈도수는 동일해야한다.

```js
same([1,2,3], [4,1,9]); // true
same([1,2,3], [1,9]); // false
same([1,2,1], [4,4,1]); // false (must be same frequency)
```

#### **Naive solution** 

```js
function same(arr1, arr2) {
  if (arr1.length !== arr2) {
    return false;
  }
  for (let i = 0; i < arr1.length; i++) {
    let correctIndex = arr2.indexOf(arr1[i] ** 2);
    if (correctIndex === -1) {
      return false;
    }
    arr2.splice(correctIndex, 1);
  }
  return true;
}
```

2중 `for`문을 사용하는 방법으로 `O(N²)`의 시간복잡도를 가진다.

#### **Refactored solution**

```js
function same(arr1, arr2) {
  if (arr1.length !== arr2.length) {
    return false;
  }
  let frequencyCounter1 = {};
  let frequencyCounter2 = {};
  for (let val of arr1) {
    frequencyCounter1[val] = (frequencyCounter1[val] || 0) + 1;
  }
  for (let val of arr2) {
    frequencyCounter2[val] = (frequencyCounter2[val] || 0) + 1;
  }
  for (let key in frequencyCounter1) {
    if (!(key ** 2 in frequencyCounter2)) {
      return false;
    }
    if (frequencyCounter2[key ** 2] !== frequencyCounter1[key]) {
      return false;
    }
    return true;
  }
}
```

`Object`를 활용하는 방법으로 `O(N)`의 시간복잡도를 가진다.

### Example : `validAnagram`

#### **Question**

두 개의 string을 매개변수로 요구하고 두 번째 매개변수가 첫 번째의 애너그램인지 판별하는 함수를 작성한다.

(애너그램은 문자를 재배열한 것을 의미한다. `iceman` -> `cinema`) 

```js
vaildAnagram('', ''); // true
vaildAnagram('aaz', 'zza'); // false
vaildAnagram('anagram', 'nagaram'); // true
vaildAnagram('rat', 'car'); // false
vaildAnagram('awesome', 'awesom'); // false
vaildAnagram('qwerty', 'qeywrt'); // true
vaildAnagram('texttwisttime', 'timetwisttext'); // true
```

#### **My solution**

```js
function validAnagram(str1, str2) {
  // 두 문자열의 길이가 다르다면 false
  if (str1.length !== str2.length) {
    return false;
  }
  let frequencyCounter1 = {};
  let frequencyCounter2 = {};
  // str1의 문자가 객체에 없다면 key를 추가하고 +1 있다면 원래 value에 +1
  for (const letter of str1) {
    frequencyCounter1[letter] = (frequencyCounter1[letter] || 0) + 1;
  }
  // str2의 문자가 객체에 없다면 key를 추가하고 +1 있다면 원래 value에 +1
  for (const letter of str2) {
    frequencyCounter2[letter] = (frequencyCounter2[letter] || 0) + 1;
  }
  // str1 객체에 대해 str2 객체와 값 비교 수행
  for (const key in frequencyCounter1) {
    // str2 객체에 str1 객체의 문자가 없다면 false
    if (!(key in frequencyCounter2)) {
      return false;
    }
    // str2 객체와 str1 객체 문자의 빈도수가 다르다면 false
    if (frequencyCounter1[key] !== frequencyCounter2[key]) {
      return false;
    }
  }
  return true;
}
```

위의 Frequency Counter를 그대로 이용해보았다.

#### **Reference soultion**

```js
function validAnagram(first, second) {
  if (first.length !== second.length) {
    return false;
  }

  const lookup = {};

  for (let i = 0; i < first.length; i++) {
    let letter = first[i];
    // if letter exists, increment, otherwise set to 1
    lookup[letter] ? (lookup[letter] += 1) : (lookup[letter] = 1);
  }

  for (let i = 0; i < second.length; i++) {
    let letter = second[i];
    // can't find letter or letter is zero then it's not an anagram
    if (!lookup[letter]) {
      return false;
    } else {
      lookup[letter] -= 1;
    }
  }

  return true;
}
```

같은 코드여도 다른 표현법이 존재한다.

`frequencyCounter1[letter] = (frequencyCounter1[letter] || 0) + 1;`를 `lookup[letter] ? (lookup[letter] += 1) : (lookup[letter] = 1);`로 쓸 수 있는 것처럼...

> 🐰 RÉFÉRENCE
> 
> [JavaScript Algorithms and Data Structures Masterclass](https://www.udemy.com/course/js-algorithms-and-data-structures-masterclass/ "JavaScript Algorithms and Data Structures Masterclass")
