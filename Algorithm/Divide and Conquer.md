## 🍋 Divide and Conquer

### Divide and Conquer 패턴

데이터를 더 작은 단위로 나누면서 문제를 해결한 뒤 이를 다시 합치는 패턴이다.

대표적으로 퀵 정렬과 병합 정렬이 이 패턴에 속한다.

> #### 🍒 MÉMO
> 이진 탐색도 Divide and Conquer 패턴의 일종이라고 한다..🥲 Multiple Pointers 패턴인 줄 알았는데..!!

### Example : `search`

#### **Question**

정렬된 정수 배열와 숫자를 매개변수로 받는 함수를 작성한다.

입력받은 숫자가 배열의 몇 번 인덱스에 있는지를 반환하고 만약 해당되는 값이 없다면 -1을 반환한다.

```js
search([1, 2, 3, 4, 5, 6], 4); // 3
search([1, 2, 3, 4, 5, 6], 6); // 5
search([1, 2, 3, 4, 5, 6], 11); // -1
```

#### **Naive solution**

```js
function search(arr, val) {
  for (let i = 0; i < arr.length; i++) {
    if (arr[i] === val) {
      return i;
    }
  }
  return -1;
}
```

`for`문을 활용한 방법으로 `O(N)`의 시간 복잡도를 가진다.

> #### 🍒 MÉMO
> **Linear Search(선형 탐색)** 라고도 불린다.

#### **Refactored solution**

```js
function search(arr, val) {
  let min = 0;
  let max = arr.length - 1;

  while (min <= max) {
    let middle = Math.floor((min + max) / 2);
    let currentElement = arr[middle];

    if (currentElement < val) {
      min = middle + 1;
    } else if (currentElement > val) {
      max = middle - 1;
    } else {
      return middle;
    }
  }
  return -1;
}
```

배열을 반으로 나눠 비교하는 방법으로 비교하는 양이 계속 줄어들기 때문에 `O(㏒N)`의 시간 복잡도를 가진다.

> #### 🍒 MÉMO
> **Binary Search(이진 탐색)** 라고도 불린다.  
> 배열의 중간값과 탐색값을 비교하여 탐색값이 더 크면(또는 작으면) 중간값 이전의(또는 이후의) 인덱스로 옮겨 다시 중간값을 찾아 비교하는 방법이다.

> #### 🐰 RÉFÉRENCE
> [JavaScript Algorithms and Data Structures Masterclass](https://www.udemy.com/course/js-algorithms-and-data-structures-masterclass/ "JavaScript Algorithms and Data Structures Masterclass")
