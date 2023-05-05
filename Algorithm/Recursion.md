## 🍋 Recursion

### Recursion

주어진 문제를 해결하기 위해 하나의 함수에서 자신을 다시 호출하여 작업을 수행하는 방식이다.

한 가지 문제를 가지고 어떤 엔드 포인트에 도달할 때까지 더 작은 부분을 반복적으로 수행한다. 이 때 해당 엔드 포인트를 베이스 케이스라고 부른다.

> #### 🍒 MÉMO
> 🧒🏻 : 목록의 숫자들이 홀수인지 알려주세요.  
> 🐲 : 난 목록의 첫 번째 숫자만 알려줄 것이다.  
> 🧒🏻 : (**3142** 5798 6550 5914) 이 목록의 첫 번째 숫자는 홀수인가요?  
> 🐲 : 그 숫자는 짝수이다.  
> 🧒🏻 : (**5798** 6550 5914) 이 목록의 첫 번째 숫자는 홀수인가요?  
> 🐲 : 그 숫자는 짝수이다.  
> 🧒🏻 : (**6550** 5914) 이 목록의 첫 번째 숫자는 홀수인가요?  
> 🐲 : 그 숫자는 짝수이다.  
> 🧒🏻 : (**5914**) 이 목록의 첫 번째 숫자는 홀수인가요?  
> 🐲 : 그 숫자는 짝수이다.  
> 🧒🏻 : () 이 목록의 첫 번째 숫자는 홀수인가요?  
> 🐲 : 목록에 아무 숫자도 없잖아!  
> 🧒🏻 : 아하! 그럼 목록의 모든 숫자는 짝수군요!  
> 🐲 : 축하한다. 재귀를 발견했구나.

### Example of recursion

재귀 함수는 내가 모르는 사이에 여기 저기서 쓰이고 있다.

-   `JSON.parse` / `JSON.stringify`
-   `document.getElementByID` / DOM 순회 알고리즘
-   객체 순회

### Call Stack

함수의 호출을 담당하는 JavaScript의 자료 구조이다.

스택이란 이름에서 알 수 있듯이, 함수를 호출하면 콜 스택의 가장 위에 위치하고 JavaScript가 `return`을 확인하거나 함수 안에서 더 이상 실행할 코드가 없으면 컴파일러가 콜 스택의 가장 위에 있는 항목을 제거한다.

```js
function takeShower() {
  return 'Showering!';
}

function eatBreakfast() {
  let meal = cookFood();
  return `Eating ${meal}`;
}

function cookFood() {
  let items = ['Oatmeal', 'Eggs', 'Protein Shake'];
  return items[Math.floor(Math.random() * items.length)];
}

function wakeUp() {
  takeShower();
  eatBreakfast();
  console.log('OK ready to go to work!');
}

wakeUp();
```
<div align="center">

  ![Call Stack 순서](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FddFHGa%2Fbtsa7tqDz6G%2FDweIuwFrqeszuKESH0yKEK%2Fimg.png)

  Call Stack 순서

</div>

일반적으로 함수를 작성할 때 콜 스택에 함수가 쌓이는 순서이다.

우선 가장 먼저 호출된 `wakeUp()`이 쌓이고, `wakeUp()`에서 호출한 `takeShower()`가 그 위에 쌓인다.

`takeShower()`가 반환되면 `eatBreakfast()`가 호출되고, `eatBreakfast()`에서 `cookFood()`를 호출하고 있기 때문에 `cookFood()`가 반환되고 `eatBreakfast()`가 반환되면서 콜 스택에는 `wakeUp()`만 남게 된다.

`wakeUp()`이 `OK ready to go to work!`를 반환하면 콜 스택에 어떤 함수도 남아있지 않는다.

그러나 **재귀 함수의 경우 함수 내에서 자기 자신을 계속 호출하기 때문에 콜 스택에 동일한 함수가 계속 추가**된다.

> #### 🐰 RÉFÉRENCE
> [JavaScript Algorithms and Data Structures Masterclass](https://www.udemy.com/course/js-algorithms-and-data-structures-masterclass/ "JavaScript Algorithms and Data Structures Masterclass")
