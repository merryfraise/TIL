## 🫐 Everyday Types

### Primitives

#### `string`

모든 문자열 타입

```ts
const name: string = 'Shoupeach';
```

#### `number`

모든 숫자 타입

```ts
const age: number = 4;
```

#### `boolean`

`true` 또는 `false` 타입

```ts
const isApeach: boolean = true;
```

#### `undefined`

`undefined`만 지정 가능한 타입

```ts
const career: undefined = undefined;
```

#### `null`

`null`만 지정 가능한 타입

```ts
const career: null = null;
```

> #### 🍒 MÉMO
> `undefined`는 값의 여부를 모르는 경우, `null`은 값이 없는 경우 사용된다. 😃

### Objects

#### `object`

모든 JavaScript 객체 타입

```ts
let obj: object;
obj = { name: 'Shoupeach', isApeach: true };
obj = [1, 2, 3, 4];
obj = () => console.log('rabbit');
```

#### `Array`

배열 타입으로 배열의 요소는 한 가지 타입으로 고정

```ts
const species: string[] = ['rabbit', 'platypus'];
const name: Array<string> = ['Shoupeach', 'Ogu'];
```

#### `Tuple`

배열 타입으로 크기가 고정된 여러 타입의 요소를 사용 가능

```ts
let shoupeach: [string, boolean];
shoupeach = ['rabbit', true];
```

> #### 🍒 MÉMO
> 크기가 고정되어 있으나 `push` 메소드는 사용이 가능하다..?! 🤪

### Others

#### `any`

어떤 타입이든 가능한 타입

```ts
let species: any = 'rabbit';
species = 4;
```

#### `unknown`

어떤 타입인지 알 수 없는 타입

```ts
let species: unknown = 'rabbit';
species = 4;
```

> #### 🍒 MÉMO
> `any`와 `unknown`은 어떤 타입이든 수용 가능하다는 점에서 같지만, `unknown`은 추가적인 타입 확인 과정을 필요로 한다는 점에서 차이가 있다.

#### `void`

일반적으로 함수에서 어떤 값도 반환하지 않을 때 사용

```ts
function printName(): void {
  console.log('Shoupeach');
}
```

> #### 🍒 MÉMO
> `console.log()`는 `return` 값이 아니라 메세지를 출력하는 함수이다. 😃

#### `never`

일반적으로 함수에서 어떤 값도 반환하지 않을 때 사용

```ts
function printError(): never {
  throw new Error('error');
}
```

> #### 🍒 MÉMO
> `void`와 `never` 타입 모두 함수에서 어떤 값도 반환하지 않을 때 사용하지만 `never`는 에러를 발생시킬 때 보통 사용한다고 한다. 🤔

#### `enum`

상수값을 부여하는 열거형 타입

```ts
enum Species {
  rabbit,
  platypus,
}

Species.rabbit; // 0
Species.platypus; // 1
```

> #### 🍒 MÉMO
> 기본적으로는 각 값들이 0부터 카운팅되고, 특정 값을 부여하는 것도 가능하다.

#### Type alias

사용자 정의 타입

```ts
type Name = string;
const name: Name = 'Shoupeach';
```

직접 특정 값을 가진 타입을 설정하는 것 또한 가능

```ts
type Name = 'Shoupeach';
const name: Name = 'Shoupeach';
// name에 'Shoupeach'가 아닌 다른 값이 들어갈 수 없음
```

#### `union`

나열한 타입 중 하나만 충족하면 되는 타입

```ts
type Shoupeach = string | boolean;
let shoupeach: Shoupeach = 'rabbit';
shoupeach = true;
```

#### `intersection`

나열한 타입을 모두 충족해야 하는 타입

```ts
type Name = {
  name: string;
}
type IsApeach = {
  isApeach: boolean;
}

const master: Name & IsApeach = { name: 'Shoupeach', isApeach: true };
```

> #### 🐰 RÉFÉRENCE
> [TypeScript 공식 문서](https://www.typescriptlang.org/docs/handbook/2/everyday-types.html "TpyeScript 공식 문서")
