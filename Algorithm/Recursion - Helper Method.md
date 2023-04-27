## 🍋 Recursion - Helper Method

### Helper Method pattern

**외부 함수에 내부 재귀 함수를 정의**하여 배열이나 데이터 목록 같은 걸 컴파일 할 때 사용하는 패턴

```js
function outer(input) {
  let outerScopedVariable = [];
  
  function helper(helperInput) {
    // modify the outerScopedVariable
    helper(helperInput--);
  }
  
  helper(input);
  
  return outerScopedVariable;
}
```

### Example : collectOddValues

#### **Question**

```js
collectOddValues([1, 2, 3, 4, 5]); // [1, 3, 5]
```

#### **Pure recursion solution**

```js
function collectOddValues(arr) {
  let newArr = [];

  if (arr.length === 0) {
    return newArr;
  }

  if (arr[0] % 2 !== 0) {
    newArr.push(arr[0]);
  }

  newArr = newArr.concat(collectOddValuesPure(arr.slice(1)));
  
  return newArr;
}
```

> #### 🍒 MÉMO
> Helper Method 패턴 없이 순수 재귀로만 함수를 작성할 경우  
> 1. Array는 immutable한 slice, concat, spread operator 등을 사용한다.  
> 2. String은 자체적으로 immutable하기 때문에 원본을 복사하는 slice, substr, substring 등을 사용한다.  
> 3. Object는 원본을 복사하는 Object.assign, spread operator 등을 사용한다.

#### **Helper method solution**

```js
function collectOddValues(arr) {
  const result = [];

  function helper(helperInput) {
    if (helperInput.length === 0) {
      return;
    }

    if (helperInput[0] % 2 !== 0) {
      result.push(helperInput[0]);
    }

    helper(helperInput.slice(1));
  }

  helper(arr);

  return result;
}
```

> #### 🐰 RÉFÉRENCE
> [JavaScript Algorithms and Data Structures Masterclass](https://www.udemy.com/course/js-algorithms-and-data-structures-masterclass/ "JavaScript Algorithms and Data Structures Masterclass")
