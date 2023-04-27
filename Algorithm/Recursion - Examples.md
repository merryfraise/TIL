## 🍋 Recursion - Examples

### Example : `countDown`

#### **Question**

```js
countDown(5);
/*
5
4
3
2
1
All done!
*/
```

#### **Loop solution**

```js
function countDown(num) {
  for (let i = num; i > 0; i--) {
    console.log(i);
  }
  console.log("All done!");
}
```

#### **Recursion solution** 

```js
function countDown(num) {
  if (num <= 0) {
    console.log('All done!');
  }
  console.log(num);
  num--;
  countDown(num);
}
```

#### **Mechanism**

![countDown](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FeofAYO%2FbtscRKevVv2%2FK7PMJPliNK02BNkrH7HPk0%2Fimg.png)
`countDown` 작동 원리

`countDown` 함수에서 `num <= 0`일 때 재귀 호출이 멈추기 때문에 베이스 케이스는 `if (num <= 0)`이다.

### Example : `sumRange`

#### **Question**

```js
sumRange(4); // 10
```

#### **Solution**

```js
function sumRange(num) {
  if (num === 1) return 1;
  return num + sumRange(num - 1);
}
```

#### **Mechanism**

![sumRange](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcgX6CS%2FbtscZaCrJXV%2Faxe1xGIIVkOBigNjKkVZH0%2Fimg.png)
`sumRange` 작동 원리

`sumRange` 함수에서 `num === 1`일 때 재귀 호출이 멈추기 때문에 베이스 케이스는 `if (num === 1)`이다.

`sumRange(3)`을 호출할 시 `return 3 + 2 + 1`이므로 6이 반환된다.

### Example : `factorial`

#### **Question**

```js
factorial(4); // 24
```

#### **Loop solution**

```js
function factorial(num) {
  let total = 1;
  for (let i = num; i > 1; i--) {
    total *= i;
  }
  return total;
}
```

#### **Recursive solution**

```js
function factorial(num) {
  if (num === 1) return 1;
  return num * factorial(num - 1);
}
```

#### **Mechanism**

![factorial](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbtkvrL%2FbtscZtofAZp%2F7a8dWLqjMOVq1Sy31ie3i1%2Fimg.png)
`factorial` 작동 원리

`factorial` 함수의 작동 원리는 `sumRange`와 동일하다. 덧셈 대신 곱셈을 해주고 있을 뿐...

> #### 🐰 RÉFÉRENCE
> [JavaScript Algorithms and Data Structures Masterclass](https://www.udemy.com/course/js-algorithms-and-data-structures-masterclass/ "JavaScript Algorithms and Data Structures Masterclass")
