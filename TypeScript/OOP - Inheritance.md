## 🫐 OOP - Inheritance

### Inheritance

상속이란 기존에 생성된 객체를 기반으로 하는 새로운 객체를 만드는 것이다.

일반적으로 **기존에 생성된 객체를 부모**, 이를 **기반으로 생성된 새로운 객체를 자식**이라고 부른다.

<div align="center">
  
  ![Inheritance](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fb3Gb7w%2FbtsdZP53Lns%2FQWnAqBK6LAsD5FiXBgsA8k%2Fimg.png)
  
  Inheritance
  
</div>

### Example

```ts
type Ingredients = {
  [key: string]: {
    sliceable: boolean;
    boilable: boolean;
  };
};

interface Cook {
  cook(): void;
}

class Cooking implements Cook {
  // 재료는 한 번 할당한 뒤 참조가 불가능 하도록 private로 선언
  constructor(private ingredients: Ingredients) {}

  // cook 메소드에서 처리하기 위해 은닉 (상속을 위해 protected로 선언)
  protected slice(): void {
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

  // cook 메소드에서 처리하기 위해 은닉 (상속을 위해 protected로 선언)
  protected boil(): void {
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

// Cooking을 상속하는 BulgogiCooking 생성
class BulgogiCooking extends Cooking {}

const bulgogi = new BulgogiCooking({
  버섯: { sliceable: true, boilable: true },
  파: { sliceable: true, boilable: true },
  고기: { sliceable: true, boilable: true },
});

bulgogi.cook();
/* 버섯 재료를 썹니다.
   파 재료를 썹니다.
   고기 재료를 썹니다.
   (5초 후)
   버섯 재료를 끓입니다.
   파 재료를 끓입니다.
   고기 재료를 끓입니다. */
```

> #### 🍒 MÉMO
> 부모의 메소드 내용을 상속하면서 새로운 내용을 덧붙이고 싶을 때는 `super` 키워드를 이용하면 된다.
