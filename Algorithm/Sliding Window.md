## 🍋 Sliding Window

### Sliding Window 패턴

배열이나 문자열과 같은 일련의 데이터에서 특정 범위의 **윈도우**가 있을 때, 윈도우 내부 요소의 값을 이용해 문제를 푸는 패턴이다.

규모가 큰 데이터에서 하위 집합을 추적하는 경우에 유용하다.

![Sliding Window](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fbbn6CN%2Fbtr8Mp6wGZz%2F8w463IYM9CNWkwqU3IcKF1%2Fimg.png)

> #### 🍒 MÉMO
> Multiple Pointers 패턴과 비슷해 보일 수 있는데, Multiple Pointers는 정렬된 배열을 요구하는 반면 **Sliding Window는 요소들의 정렬 여부와 관계 없이 사용**할 수 있다.

### Example : `maxSubarraySum`

#### **Question**

정수 배열과 숫자 하나(n)를 매개변수로 요구하는 함수를 작성한다.

배열 내의 서로 마주한 n개의 숫자를 더한 값 중 가장 큰 값을 반환해야 한다.

```js
maxSubarraySum([1, 2, 5, 2, 8, 1, 5], 2); // 10
maxSubarraySum([1, 2, 5, 2, 8, 1, 5], 4); // 17
maxSubarraySum([4, 2, 1, 6], 1); // 6
maxSubarraySum([4, 2, 1, 6, 2], 4); // 13
maxSubarraySum([], 4); // null
```

#### **Naive solution**

```js
function maxSubarraySum(arr, num) {
  if (num > arr.length) {
    return null;
  }
  let max = -Infinity;
  for (let i = 0; i < arr.length - num + 1; i++) {
    let temp = 0;
    for (let j = 0; j < num; j++) {
      temp += arr[i + j];
    }
    if (temp > max) {
      max = temp;
    }
  }
  return max;
}
```

2중 `for`문을 활용한 방법으로 `O(N²)`의 시간 복잡도를 가진다.

> #### 🍒 MÉMO
> 초기에 `max = -Infinity`로 설정한 이유는 배열의 요소만큼 더한 값이 음수일 수도 있기 때문인 것 같다. 요소의 합이 양수가 아니라면 `max = 0`으로 설정했을 때 결과값에 차이가 있을 것이다.

#### **Refactored solution**

```js
function maxSubarraySum(arr, num) {
  let maxSum = 0;
  let tempSum = 0;
  if (arr.length < num) return null;
  for (let i = 0; i < num; u++) {
    maxSum += arr[i];
  }
  tempSum = maxSum;
  for (let i = num; i < arr.length; i++) {
    tempSum = tempSum - arr[i - num] + arr[i];
    maxSum = Math.max(maxSum, tempSum);
  }
  return maxSum;
}
```

`for`문을 중첩하지 않은 방법으로 `O(N)`의 시간 복잡도를 가진다.

> #### 🍒 MÉMO
> `maxSum`을 `arr[0]`부터 `arr[num - 1]`까지 더한 값으로 우선 할당한 뒤, 배열을 이동하며 현재 위치한 **윈도우** 바로 이전에 있는 요소를 빼고, **윈도우** 내부의 가장 마지막 값을 더해 `maxSum`을 다시 판별하게 하였다.  
> **윈도우**의 크기가 4라면 `arr[0] + arr[1] + arr[2] + arr[3]`을 `maxSum`과 `tempSum`에 할당해두었다가 **윈도우**를 옮기면서 `arr[0] + arr[1] + arr[2] + arr[3] **- arr[0] + arr[4]**`를 수행한 격

> #### 🐰 RÉFÉRENCE
> [JavaScript Algorithms and Data Structures Masterclass](https://www.udemy.com/course/js-algorithms-and-data-structures-masterclass/ "JavaScript Algorithms and Data Structures Masterclass")  
> [Sliding Window](https://takeuforward.org/data-structure/sliding-window-technique/ "Sliding Window")
