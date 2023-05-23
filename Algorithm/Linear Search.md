## 🍋 Linear Search

### Linear Search

주어진 배열에서 **모든 요소를 살펴 보면서 원하는 값이 있는지 확인**하는 가장 간단한 방법의 탐색이다.

> #### 🍒 MÉMO
> JavaScript에는 배열에서 사용할 수 있는 다양한 탐색용 메소드가 존재한다.  
> 
> -   `indexOf`
> -   `includes`
> -   `find`
> -   `findIndex`

### Method Example

```js
const animal = ['rabbit', 'platypus', 'cat', 'dog'];

/* indexOf */
animal.indexOf('rabbit'); // 0
animal.indexOf('dog'); // 3
animal.indexOf('bird'); // -1

/* includes */
animal.includes('platypus'); // true
animal.includes('deer'); // false
```

### Example : `linearSearch`

#### **Question**

배열과 하나의 숫자를 매개변수로 요구하는 함수를 작성한다.

함수는 배열에 해당 숫자가 존재한다면 숫자의 인덱스를 반환하고, 숫자가 존재하지 않는다면 -1을 반환한다.

```js
linearSearch([10, 15, 20, 25, 30], 15); // 1
linearSearch([9, 8, 7, 6, 5, 4, 3, 2, 1, 0], 4); // 5
linearSearch([100], 100); // 0
linearSearch([1, 2, 3, 4, 5], 6); // -1
linearSearch([9, 8, 7, 6, 5, 4, 3, 2, 1, 0], 10); // -1
linearSearch([100], 200); // -1
```

> #### 🍒 MÉMO
> `indexOf` 메소드가 이 알고리즘을 사용한다.

#### **My solution**

```js
function linearSearch(nums, value) {
  for (let i = 0; i < nums.length; i++) {
    if (nums[i] === value) return i;
  }
  return -1;
}
```

#### **Reference solution**

```js
function linearSearch(arr, val) {
  for (var i = 0; i < arr.length; i++) {
    if (arr[i] === val) return i;
  }
  return -1;
}
```

### Big O

일반적으로 Linear Search의 시간복잡도는 `O(N)`이다. 배열의 길이가 길어질수록 탐색하는 양이 많아지기 때문이다.

<div align="center">
  
  ![Big O](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FII5jO%2Fbtsg8cXSmiJ%2FLhmnQutt4Csm5KH9zkzBwK%2Fimg.png)
  
  Linear Search의 Big O
  
</div>

> #### 🍒 MÉMO
> `O(N)`이 선형 그래프를 보이기 때문에 Linear Search라고 부른다.

#### **Best**

찾고 있는 값을 곧바로 찾는 경우가 최고의 케이스이기 때문에 `O(1)`이다.

#### **Average**

일반적으로 배열의 길이가 길어질수록 평균 소요 시간이 증가하기 때문에 평균도 `O(N)`이다.

#### **Worst**

마지막 값을 찾고 있거나 배열에 포함되지 않은 값을 찾는 경우 전체 배열을 탐색해야 하기 때문의 최악의 케이스는 `O(N)`이다.

> #### 🐰 RÉFÉRENCE
> [JavaScript Algorithms and Data Structures Masterclass](https://www.udemy.com/course/js-algorithms-and-data-structures-masterclass/ "JavaScript Algorithms and Data Structures Masterclass")
