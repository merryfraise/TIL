## 🍋 Binary Search

### Binary Search

Linear Search가 모든 항목을 탐색하는 방법이었다면, Binary Search는 그 보다 훨씬 빠른 형태의 탐색 방법이다.

Binary Search는 **한 번 확인할 때마다 남은 항목의 절반을 없앨 수 있다**.

단, Binary Search는 **정렬된 배열에서만 사용**할 수 있다.

> #### 🍒 MÉMO
> Binary Search에 사용되는 주요 개념은 [Divide and Conquer](https://github.com/merryfraise/TIL/blob/main/Algorithm/Divide%20and%20Conquer.md)이다.

### Example : `binarySearch`

#### **Question**

정렬된 배열과 하나의 값을 매개변수로 요구하는 함수를 작성한다.

함수는 인자로 들어온 값이 배열에 존재하면 해당 인덱스를 반환하고, 존재하지 않는다면 -1을 반환한다.

```js
binarySearch([1, 2, 3, 4, 5], 2); // 1
binarySearch([1, 2, 3, 4, 5], 3); // 2
binarySearch([1, 2, 3, 4, 5], 5); // 4
binarySearch([1, 2, 3, 4, 5], 6); // -1
binarySearch([5, 6, 10, 13, 14, 18, 30, 34, 35, 37, 40, 44, 64, 79, 84, 86, 95, 96, 98, 99], 10); // 2
binarySearch([5, 6, 10, 13, 14, 18, 30, 34, 35, 37, 40, 44, 64, 79, 84, 86, 95, 96, 98, 99], 95); // 16
binarySearch([5, 6, 10, 13, 14, 18, 30, 34, 35, 37, 40, 44, 64, 79, 84, 86, 95, 96, 98, 99], 100); // -1
```

#### **My solution**

```js
function binarySearch(arr, val) {
  let left = 0;
  let right = arr.length - 1;

  while (left <= right) {
    let mid = Math.floor((left + right) / 2);

    if (val < arr[mid]) right = mid - 1;
    else if (val > arr[mid]) left = mid + 1;
    else return mid;
  }

  return -1;
}
```

#### **Reference solution**

```js
function binarySearch(arr, elem) {
  var start = 0;
  var end = arr.length - 1;
  var middle = Math.floor((start + end) / 2);

  while (arr[middle] !== elem && start <= end) {
    if (elem < arr[middle]) end = middle - 1;
    else start = middle + 1;
    middle = Math.floor((start + end) / 2);
  }

  return arr[middle] === elem ? middle : -1;
}
```

### Big O

일반적으로 Binary Search의 시간복잡도는 `O(logN)`이다.

배열의 요소가 16개인 경우 최대 4단계를 거쳐 탐색을 할 수 있고, 32개인 경우 최대 5단계를 거쳐 탐색을 할 수 있다.

<div align="center">
  
  ![O(logN)](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcztQFd%2Fbtsg3ViyFPZ%2FgiJYxELsJnIyFDN9U8oJuK%2Fimg.png)
  
  O(logN)
  
  ![Big O](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2F0OO4s%2Fbtsg3WhmNYI%2FXDPrzFGF0P1bSd8otjDPuk%2Fimg.png)
  
  Binary Search의 Big O
  
</div>

#### **Best**

찾고 있는 값을 곧바로 찾는 케이스로 `O(1)`이다.

#### **Average**

배열의 길이가 길어질 수록 평균 소요 시간도 증가하기 때문에 `O(logN)`이다.

#### **Worst**

마지막 값을 찾거나 존재하지 않는 값을 찾는 경우 모든 케이스를 살펴봐야하는데, Binary Search의 경우 `O(logN)`의 복잡도를 가진다.

> #### 🐰 RÉFÉRENCE
> [JavaScript Algorithms and Data Structures Masterclass](https://www.udemy.com/course/js-algorithms-and-data-structures-masterclass/ "JavaScript Algorithms and Data Structures Masterclass")
