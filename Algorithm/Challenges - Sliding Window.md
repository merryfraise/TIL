## 🍋 Challenges - Sliding Window

### Example : `maxSubarraySum`

#### **Question**

정수 숫자 배열과 숫자 한 개(n)를 매개변수로 요구하는 함수를 작성한다.

배열의 하위 배열의 합 중 최댓값을 반환해야 하며 하위 배열의 길이는 n이다.

(하위 배열은 원본 배열로부터 **연속된** 요소로 구성된 배열을 의미한다. `[100, 200, 300, 400]`의 하위배열 -> `[100, 200, 300]` ⭕️ `[100, 300]` ❌)

```js
maxSubarraySum([100, 200, 300, 400], 2); // 700
maxSubarraySum([1, 4, 2, 10, 23, 3, 1, 0, 20], 4); // 39
maxSubarraySum([3, -2, 7, -4, 1, -1, 4, -2, 1], 2); // 5
maxSubarraySum([2, 3], 3); // null
```

#### **My solution**

```js
function maxSubarraySum(arr, num) {
  if (arr.length < num) return null;

  let maxSum = 0;
  let curSum = 0;

  // 초기 maxSum
  for (let i = 0; i < num; i++) {
    maxSum += arr[i];
  }
  // 현재 curSum
  curSum = maxSum;

  // 반복문 돌면서 현재 curSum과 maxSum 비교하여 필요하면 값 교체
  for (let i = num; i < arr.length; i++) {
    curSum = curSum - arr[i - num] + arr[i];
    if (maxSum < curSum) maxSum = curSum;
  }
  return maxSum;
}
```

#### **Reference solution**

```js
function maxSubarraySum(arr, num){
  if (arr.length < num) return null;

  let total = 0;
  for (let i=0; i<num; i++){
     total += arr[i];
  }
  let currentTotal = total;
  for (let i = num; i < arr.length; i++) {
     currentTotal += arr[i] - arr[i-num];
     total = Math.max(total, currentTotal);
  }
  return total;
}
```

### Example : `minSubarrayLen`

#### **Question**

양의 정수 배열과 양의 정수 한 개(n)를 매개변수로 요구하는 함수를 작성한다.

**인접한** 하위 배열의 요소의 합이 n이상인 것들 중 가장 짧은 하위 배열의 길이를 반환해야 한다.

일치하는 것이 존재하지 않는다면 0을 반환한다.

```js
minSubarrayLen([2, 3, 1, 2, 4, 3], 7); // 2 -> because [4, 3] is the smallest subarray
minSubarrayLen([2, 1, 6, 5, 4], 9); // 2 -> because [5, 4] is the smallest subarray
minSubarrayLen([3, 1, 7, 11, 2, 9, 8, 2, 1, 62, 33, 19], 52); // 1 ->  because [62] is greater than 52
minSubarrayLen([1, 4, 16, 22, 5, 7, 8, 9, 10], 39); // 3
minSubarrayLen([1, 4, 16, 22, 5, 7, 8, 9, 10], 55); // 5
minSubarrayLen([4, 3, 3, 8, 1, 2, 3], 11); // 2
minSubarrayLen([1, 4, 16, 22, 5, 7, 8, 9, 10], 95); // 0
```

#### **Reference solution**

```js
function minSubarrayLen(nums, sum) {
  let total = 0;
  let start = 0;
  let end = 0;
  let minLen = Infinity;
 
  while (start < nums.length) {
    // if current window doesn't add up to the given sum then 
		// move the window to right
    if(total < sum && end < nums.length){
      total += nums[end];
			end++;
    }
    // if current window adds up to at least the sum given then
		// we can shrink the window 
    else if(total >= sum){
      minLen = Math.min(minLen, end-start);
			total -= nums[start];
			start++;
    } 
    // current total less than required total but we reach the end, need this or else we'll be in an infinite loop 
    else {
      break;
    }
  }
 
  return minLen === Infinity ? 0 : minLen;
}
```

### Example : `findLongestSubstring`

#### **Question**

문자열을 매개변수로 요구하는 함수를 작성한다.

문자열 중에서 가장 긴 하위 문자열의 길이를 반환한다.

```js
findLongestSubstring(''); // 0
findLongestSubstring('rithmschool'); // 7
findLongestSubstring('thisisawesome'); // 6
findLongestSubstring('thecatinthehat'); // 7
findLongestSubstring('bbbbbb'); // 1
findLongestSubstring('longestsubstring'); // 8
findLongestSubstring('thisishowwedoit'); // 6
```

#### **Reference solution**

```js
function findLongestSubstring(str) {
  let longest = 0;
  let seen = {};
  let start = 0;
 
  for (let i = 0; i < str.length; i++) {
    let char = str[i];
    if (seen[char]) {
      start = Math.max(start, seen[char]);
    }
    // index - beginning of substring + 1 (to include current in count)
    longest = Math.max(longest, i - start + 1);
    // store the index of the next char so as to not double count
    seen[char] = i + 1;
  }
  return longest;
}
```

> #### 🐰 RÉFÉRENCE
> [JavaScript Algorithms and Data Structures Masterclass](https://www.udemy.com/course/js-algorithms-and-data-structures-masterclass/ "JavaScript Algorithms and Data Structures Masterclass")
