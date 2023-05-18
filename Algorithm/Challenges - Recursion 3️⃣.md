## 🍋 Challenges - Recursion 3️⃣

### Example : `capitalizeFirst`

#### **Question**

문자열을 요소로 가진 배열을 매개변수로 요구하는 재귀 함수를 작성한다.

함수는 각 문자열의 첫번째 글자를 대문자로 변환한 문자열 배열을 반환한다.

```js
capitalizeFirst(['car', 'taco', 'banana']); // ['Car', 'Taco', 'Banana']
```

#### **My solution**

```js
function capitalizeFirst(strs) {
  if (strs.length === 0) return [];

  let upperStr = '';
  for (let i = 0; i < strs[0].length; i++) {
    if (i === 0) upperStr = strs[0][i].toUpperCase();
    else upperStr = upperStr.concat(strs[0][i]);
  }

  return [upperStr].concat(capitalizeFirst(strs.slice(1)));
}
```

#### **Reference solution**

```js
function capitalizeFirst (array) {
  if (array.length === 1) {
    return [array[0][0].toUpperCase() + array[0].substr(1)];
  }
  const res = capitalizeFirst(array.slice(0, -1));
  const string = array.slice(array.length - 1)[0][0].toUpperCase() + array.slice(array.length-1)[0].substr(1);
  res.push(string);
  return res;
}
```

### Example : `nestedEvenSum`

#### **Question**

중첩된 객체를 매개변수로 요구하는 재귀 함수를 작성한다.

함수는 객체 내에 있는 모든 짝수를 더해서 반환한다.

```js
var obj1 = {
  outer: 2,
  obj: {
    inner: 2,
    otherObj: {
      superInner: 2,
      notANumber: true,
      alsoNotANumber: 'yup',
    },
  },
};

var obj2 = {
  a: 2,
  b: { b: 2, bb: { b: 3, bb: { b: 2 } } },
  c: { c: { c: 2 }, cc: 'ball', ccc: 5 },
  d: 1,
  e: { e: { e: 2 }, ee: 'car' },
};

nestedEvenSum(obj1); // 6
nestedEvenSum(obj2); // 10
```

#### **My solution**

```js
function nestedEvenSum(obj) {
  const arr = Object.entries(obj);

  if (!arr.length) return 0;

  let sum = 0;

  for (const el of arr) {
    let key = el[0];
    let value = el[1];

    if (typeof value === 'number' && !(value % 2)) {
      sum += value;
    } else if (typeof value === 'object') sum += nestedEvenSum(value);
  }

  return sum;
}
```

#### **Reference solution**

```js
function nestedEvenSum (obj, sum=0) {
    for (var key in obj) {
        if (typeof obj[key] === 'object'){
            sum += nestedEvenSum(obj[key]);
        } else if (typeof obj[key] === 'number' && obj[key] % 2 === 0){
            sum += obj[key];
        }
    }
    return sum;
}
```

### Example : `caplitalizeWords`

#### **Question**

문자열을 요소로 가진 배열을 매개변수로 요구하는 함수를 작성한다.

함수는 각 단어를 대문자로 변환한 문자열을 요소로 가진 새 배열을 반환한다.

#### **My solution**

```js
function capitalizeWords(words) {
  if (!words.length) return [];

  const capitalWord = words[0].toUpperCase();

  return [capitalWord].concat(capitalizeWords(words.slice(1)));
}
```

#### **Reference solution**

```js
function capitalizeWords (array) {
  if (array.length === 1) {
    return [array[0].toUpperCase()];
  }
  let res = capitalizeWords(array.slice(0, -1));
  res.push(array.slice(array.length-1)[0].toUpperCase());
  return res;
}
```

### Example : `stringifyNumbers`

#### **Question**

객체를 매개변수로 요구하는 함수를 작성한다.

함수는 객체 내부의 모든 `number` 타입 값을 `string` 타입으로 변환한 객체를 반환한다.

```js
let obj = {
  num: 1,
  test: [],
  data: {
    val: 4,
    info: {
      isRight: true,
      random: 66,
    },
  },
};

stringifyNumbers(obj);
/*
{
    num: "1",
    test: [],
    data: {
        val: "4",
        info: {
            isRight: true,
            random: "66"
        }
    }
}
*/
```

#### **My solution**

```js
function stringifyNumbers(obj) {
  if (!Object.keys(obj).length) return {};

  const stringifiedObj = {};

  for (const el in obj) {
    let key = el;
    let value = obj[el];

    if (typeof value === 'number') {
      value = value.toString();
    } else if (typeof value === 'object' && !Array.isArray(value)) {
      value = stringifyNumbers(value);
    }

    stringifiedObj[key] = value;
  }

  return stringifiedObj;
}
```

#### **Reference solution**

```js
function stringifyNumbers(obj) {
  var newObj = {};
  for (var key in obj) {
    if (typeof obj[key] === 'number') {
      newObj[key] = obj[key].toString();
    } else if (typeof obj[key] === 'object' && !Array.isArray(obj[key])) {
      newObj[key] = stringifyNumbers(obj[key]);
    } else {
      newObj[key] = obj[key];
    }
  }
  return newObj;
}
```

### Example : `collectStrings`

#### **Question**

객체를 매개변수로 요구하는 함수를 작성한다.

함수는 객체에 있는 모든 문자열을 배열에 담아 반환한다.

```js
const obj = {
  stuff: 'foo',
  data: {
    val: {
      thing: {
        info: 'bar',
        moreInfo: {
          evenMoreInfo: {
            weMadeIt: 'baz',
          },
        },
      },
    },
  },
};

collectStrings(obj); // ['foo', 'bar', 'baz']
```

#### **My solution**

```js
function collectStrings(obj) {
  let result = [];

  for (const el in obj) {
    let key = el;
    let value = obj[el];

    if (typeof value === 'string') value = value;
    else if (typeof value === 'object' && !Array.isArray(value))
      value = collectStrings(value);

    result = result.concat(value);
  }

  return result;
}
```

#### **Reference solution**

```js
// Helper method recursion
function collectStrings(obj) {
    var stringsArr = [];
 
    function gatherStrings(o) {
        for(var key in o) {
            if(typeof o[key] === 'string') {
                stringsArr.push(o[key]);
            }
            else if(typeof o[key] === 'object') {
                return gatherStrings(o[key]);
            }
        }
    }
 
    gatherStrings(obj);
 
    return stringsArr;
}
```

```js
// Pure recursion
function collectStrings(obj) {
    var stringsArr = [];
    for(var key in obj) {
        if(typeof obj[key] === 'string') {
            stringsArr.push(obj[key]);
        }
        else if(typeof obj[key] === 'object') {
            stringsArr = stringsArr.concat(collectStrings(obj[key]));
        }
    }
 
    return stringsArr;
}
```

> #### 🐰 RÉFÉRENCE
> [JavaScript Algorithms and Data Structures Masterclass](https://www.udemy.com/course/js-algorithms-and-data-structures-masterclass/ "JavaScript Algorithms and Data Structures Masterclass")
