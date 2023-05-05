## 🫐 OOP - Abstraction

### Abstraction

객체 내부의 구현이 어떻게 되어있는지 알 수 없어도 사용할 수 있는 것, 즉 객체의 공통적인 속성과 기능을 정의하여 추출하는 것을 추상화라고 한다.

<div align="center">

  ![Abstraction](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fc9pR82%2Fbtr94xn82fk%2Fa8nBiynYBKbbl3KJTcI2ck%2Fimg.png)
  
  Abstraction
  
</div>

앞선 [OOP - Encapsulation](https://github.com/merryfraise/TIL/blob/main/TypeScript/OOP%20-%20Encapsulation.md)에서 `slice()`와 `boil()`이라는 메소드를 구현해보았다.

사용자는 Cooking의 `slice()`와 `boil()`이 어떻게 구현되어 있는지는 몰라도 해당 메소드를 실행하면 썰고 끓일 수 있다는 것을 알 수 있다.

하지만 요리를 하는데 있어서 `slice()`와 `boil()` 말고도 다른 여러 과정들이 있을 수 있는데 그 경우 또 다른 메소드를 만들어 이 과정들을 한꺼번에 실행하도록 다시 추상화 해줄 수 있다.

### Interface

인터페이스는 특정 객체의 역할을 정의해 수행해야 하는 핵심적인 역할만 규정해놓고 구현은 해당 인터페이스를 구현하는 객체에 맡기는 것이다.

```ts
interface Cook {
  cook(): void;
}

class Cooking implements Cook {
  constructor(private ingredients: string) {}
  
  slice(): void {}
  
  boil(): void{}
  
  cook(): void {
    this.slice();
    this.boil();
  }
}

const cooking1: Cooking = new Cooking('라면');
cooking1.slice(); // 호출 가능 ⭕️
cooking1.boil(); // 호출 가능 ⭕️
cooking1.cook(); // 호출 가능 ⭕️

const cooking2: Cook = new Cooking('볶음밥');
cooking2.slice(); // 호출 불가능 ❌
cooking2.boil(); // 호출 불가능 ❌
cooking2.cook(); // 호출 가능 ⭕️
```

인터페이스에 `cook()` 메소드를 규정하고 Cooking 클래스와 Cook 인터페이스를 각각 타입으로 가지는 인스턴스를 생성하였다.

Cooking 클래스를 타입으로 가지는 cooking1의 경우 Cooking 내에 모든 메소드가 정의되어 있기 때문에 3가지 메소드를 전부 호출 가능하지만,

Cook 인터페이스를 타입으로 가지는 cooking2는 인터페이스 내부에 `slice()`와 `boil()` 메소드 규정이 되어있지 않기 때문에 정보를 은닉시키며 규정된 `cook()`만 호출이 가능하다.

또한 인터페이스를 통해 Cooking 외의 다른 클래스를 만들었을 때, 해당 클래스 내에서 그 클래스에 맞는 방법으로 `cook()` 메소드를 구현할 수 있기 때문에 추상화에 용이하다.

### Example

```ts
type Ingredients = {
  [key: string]: {
    sliceable: boolean;
    boilable: boolean;
  };
};

class Cooking {
  // 재료는 한 번 할당한 뒤 참조가 불가능 하도록 private로 선언
  constructor(private ingredients: Ingredients) {}

  // cook 메소드에서 처리하기 위해 은닉
  private slice(): void {
    const canSlice: string[] = [];

    for (const ingredient in this.ingredients) {
      if (this.ingredients[ingredient].sliceable) {
        canSlice.push(ingredient);
      }
    }
    for (const ingredient of canSlice) {
      console.log(`${ingredient} 재료를 썹니다.`);
    }
  }

  // cook 메소드에서 처리하기 위해 은닉
  private boil(): void {
    const canBoil: string[] = [];

    for (const ingredient in this.ingredients) {
      if (this.ingredients[ingredient].boilable) {
        canBoil.push(ingredient);
      }
    }
    for (const ingredient of canBoil) {
      console.log(`${ingredient} 재료를 끓입니다.`);
    }
  }
  
  cook(): void {
    this.slice();
    setTimeout(() => {
      this.boil();
    }, 5000);
  }
}

const ramyeon = new Cooking({
  봉지라면: { sliceable: false, boilable: true },
  버섯: { sliceable: true, boilable: true },
  콩나물: { sliceable: false, boilable: true },
});

ramyeon.cook();
/* 버섯 재료를 썹니다.
   (5초 뒤)
   봉지라면 재료를 끓입니다.
   버섯 재료를 끓입니다.
   콩나물 재료를 끓입니다. */
```

> #### 🍒 MÉMO
> 인터페이스를 사용하지 않고 추상화

> #### 🐰 RÉFÉRENCE
> [객체 지향 프로그래밍의 4가지 특징ㅣ추상화, 상속, 다형성, 캡슐화](https://www.codestates.com/blog/content/%EA%B0%9D%EC%B2%B4-%EC%A7%80%ED%96%A5-%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D-%ED%8A%B9%EC%A7%95 "객체 지향 프로그래밍의 4가지 특징ㅣ추상화, 상속, 다형성, 캡슐화")
