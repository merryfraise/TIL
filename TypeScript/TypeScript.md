## 🫐 TypeScript 맛보기 😋

### TypeScript가 뭔데?!

TypeScript는 JavaScript를 기반으로 **정적 타입 문법을 추가**한 언어이다.

JavaScript는 런타임 시에 타입이 결정되는 동적인 특징을 갖고 있는데, 이를 컴파일타임 시에 타입이 지정되도록 정적으로 변환한 것이 바로 TypeScript이다.

```js
let name = 'Shoupeach';
name = true;

/* 런타임시에 타입이 결정되기 때문에
string에서 boolean으로 변경해도 문제가 없다! */
```

```ts
let name: string = 'Shoupeach';
name = true; // 🚨 error occurred 🚨

/* 컴파일시에 타입이 결정되기 때문에
string에서 boolean으로 변경할 시 에러가 발생한다 ㅠㅠ */
```

### TypeScript 설치하기

#### 현재 진행중인 프로젝트에만 설치하고 싶다면

```bash
# using npm
npm install typescript --save-dev

# using yarn
yarn add typescript --dev
```

#### 전역적으로 설치하고 싶다면

```bash
# using npm
npm install typescript -g

# using yarn
yarn global add typescript
```

### tsc 기초 명령어

TypeScript 설치를 마쳤다면 `tsc` 명령어를 사용할 수 있다!

#### `tsc -h`
`tsc`를 이용한 명령어 목록을 확인하기

```bash
tsc -h
tsc --help
```

#### `tsc -v`
TypeScript의 버전 확인하기

```bash
tsc -v
tsc --version
```

#### `tsc file-name`
ts 파일을 js 파일로 컴파일하기

```bash
tsc file-name.ts
```

<div align="center">
  <img width="498" alt="스크린샷 2023-04-05 오후 11 15 47" src="https://user-images.githubusercontent.com/121331811/230118821-badcb0a0-6143-49a3-a081-08e208fb2431.png">
  
  tsc file-name.ts 사용시 주의사항!!
</div>

> #### 🍒 MÉMO
> 
> `tsc file-name.ts`으로 컴파일을 할 경우 tsconfig.json의 설정을 무시하고 기본 컴파일 옵션으로 컴파일된다.  
> (Ignoring tsconfig.json, compiles the specified files with default compiler options.)

#### `tsc -w`
자동 컴파일하기

```
tsc -w
tsc --watch
```

> #### 🍒 MÉMO
> 
> 작성한 ts 파일에 변화가 있을 때마다 `tsc file-name.ts`를 실행해야 컴파일 된 js 파일에도 변화가 적용된다.  
> 이 때, `tsc -w`를 사용해 watch mode를 작동시키면 ts 파일에 변화가 감지될 때마다 자동으로 js 파일로 컴파일을 한다.

> #### 🐰 RÉFÉRENCE
> [TypeScript 공식 문서](https://www.typescriptlang.org/ "TypeScript 공식 문서")
