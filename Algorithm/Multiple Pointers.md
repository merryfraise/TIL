## 🍋 Multiple Pointers

### Multiple Pointers 패턴

`Array`의 인덱스나 특정 위치에 해당하는 **포인터**를 2개 만든 뒤, 특정 조건에 따라 방향을 움직이며 값을 비교하는 패턴이다.

> #### 🍒 MÉMO
> 설명만 봤을 때는 이진 탐색 등의 방법에 해당하는 패턴인 것 같다!

### Example : `sumZero`

#### **Question**

오름차순으로 정렬된 정수값이 담긴 배열을 매개변수로 요구하는 함수를 작성한다.

두 수의 합이 0이 되는 첫번째 쌍을 배열로 반환해야 한다.

0이 되는 쌍이 존재하지 않는다면 `undefined`를 반환한다.

``` js
sumZero([-3, -2, -1, 0, 1, 2, 3]); // [-3, 3]
sumZero([-2, 0, 1, 3]); // undefined
sumZero([1, 2, 3]); // undefined
```

#### **Naive solution**

``` js
function sumZero(arr) {
  for (let i = 0; i < arr.length; i++) {
    for (let j = i + 1; j < arr.length; j++) {
      if (arr[i] + arr[j] === 0) {
        return [arr[i], arr[j]];
      }
    }
  }
}
```

2중 `for`문을 활용한 방법으로 `O(N²)`의 시간 복잡도와 `O(1)`의 공간 복잡도를 가진다.

#### **Refactored solution**

```js
function sumZero(arr) {
  let left = 0;
  let right = arr.length - 1;
  while (left < right) {
    let sum = arr[left] + arr[right];
    if (sum === 0) {
      return [arr[left], arr[right]];
    } else if (sum > 0) {
      right--;
    } else {
      left++;
    }
  }
}
```

`while`문을 활용한 방법으로 `O(N)`의 시간 복잡도와 `O(1)`의 공간 복잡도를 가진다.

> #### 🍒 MÉMO
> `for`문처럼 모든 요소를 탐색하는 것이 아니라, 더한 값이 0보다 크면 오른쪽 포인터의 숫자를 줄이고, 더한 값이 0보다 작으면 왼쪽 포인터의 숫자를 키우는 방법이다.

#### **Example : `countUniqueValues`**

#### **Question**

오름차순으로 정렬된 정수 배열을 매개변수로 요구하고 해당 배열의 고유값이 몇 개인지 판별하는 함수를 작성한다.

음수가 있을 수 있지만 값은 정렬되어 있어야 한다!

```js
countUniqueValues([1, 1, 1, 1, 1, 2]); // 2
countUniqueValues([1, 2, 3, 4, 4, 4, 7, 7, 12, 12, 13]); // 4
countUniqueValues([]); // 0
countUniqueValues([-2, -1, -1, 0, 1]); // 4
```

#### **My solution**

```js
function countUniqueValues(arr) {
  // 배열에 아무 것도 없거나 하나만 있을 때
  if (arr.length === 0) return 0;
  if (arr.length === 1) return 1;

  // 2개의 포인터 지정
  let current = 0;
  let compare = 1;
  let count = 1;
  // 비교용 포인터가 배열의 길이보다 작을 때까지 반복
  while (compare < arr.length) {
    // 현재 포인터와 비교용 포인터의 값이 동일하면
    if (arr[current] === arr[compare]) {
      // 비교용 포인터 이동
      compare++;
    }
    // 현재 포인터와 비교용 포인터의 값이 다르면
    else {
      // 카운트 증가
      count++;
      // 현재 포인터 이동
      current++;
      // 현재 포인터 값 비교용 포인터로 변경
      arr[current] = arr[compare];
      // 비교용 포인터 이동
      compare++;
    }
  }
  return count;
}
```

선생님의 힌트를 참고하여 코드를 작성해보았다.

#### **Reference solution**

```js
function countUniqueValues(arr) {
  if (arr.length === 0) return 0;
  let i = 0;
  for (let j = 1; j < arr.length; j++) {
    if (arr[i] !== arr[j]) {
      i++;
      arr[i] = arr[j];
    }
  }
  return i + 1;
}
```

포인터가 2개라고 해서 `for`문을 사용하지 못한다는 법은 없다...🥹 여러 케이스를 계속 공부해봐야 할 것 같다.

> #### 🐰 RÉFÉRENCE
> [JavaScript Algorithms and Data Structures Masterclass](https://www.udemy.com/course/js-algorithms-and-data-structures-masterclass/ "JavaScript Algorithms and Data Structures Masterclass")
