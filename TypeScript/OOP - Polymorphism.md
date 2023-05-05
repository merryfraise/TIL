## 🫐 OOP - Polymorphism

### Poltmorphism

다형성은 같은 함수가 다양한 형태를 지니고 있는 것을 의미한다.

<div align="center">
  
![Plymorphism](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FdWUFaB%2FbtsdZi8PoXG%2FJzke8kyuvhv606E07gDfKK%2Fimg.png)
Polymorphism

</div>

같은 `slice()`여도 고기와 배추를 써는 법은 다르기 때문에 각 객체마다 `slice()`의 동작은 다를 수 있다.

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
  constructor(protected ingredients: Ingredients) {}

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

class BulgogiCooking extends Cooking {
  slice(): void {
    const canSlice: string[] = [];

    for (const ingredient in this.ingredients) {
      if (this.ingredients[ingredient].sliceable) {
        canSlice.push(ingredient);
      }
    }
    for (const ingredient of canSlice) {
      if (ingredient === '고기') {
        console.log('고기의 힘줄과 기름기를 제거합니다.');
        console.log('0.2cm의 두께로 결 반대로 썹니다.');
      } else console.log(`${ingredient} 재료를 썹니다.`);
    }
  }
}

class KimchiCooking extends Cooking {
  slice(): void {
    const canSlice: string[] = [];

    for (const ingredient in this.ingredients) {
      if (this.ingredients[ingredient].sliceable) {
        canSlice.push(ingredient);
      }
    }
    for (const ingredient of canSlice) {
      if (ingredient === '배추') {
        console.log('배추의 밑동과 겉잎을 자릅니다.');
        console.log('배추를 밑동부터 세로 방향으로 반으로 가릅니다.');
      } else console.log(`${ingredient} 재료를 썹니다.`);
    }
  }

  cook(): void {
    this.slice();
  }
}

const bulgogi = new BulgogiCooking({
  버섯: { sliceable: true, boilable: true },
  파: { sliceable: true, boilable: true },
  고기: { sliceable: true, boilable: true },
});

const kimchi = new KimchiCooking({
  파: { sliceable: true, boilable: false },
  무: { sliceable: true, boilable: false },
  배추: { sliceable: true, boilable: false },
});

bulgogi.cook();
/* 버섯 재료를 썹니다.
   파 재료를 썹니다.
   고기의 힘줄과 기름기를 제거합니다.
   0.2cm의 두께로 결 반대로 썹니다.
   (5초 후)
   버섯 재료를 끓입니다.
   파 재료를 끓입니다.
   고기 재료를 끓입니다. */

kimchi.cook();
/* 파 재료를 썹니다.
   무 재료를 썹니다.
   배추의 밑동과 겉잎을 자릅니다.
   배추를 밑동부터 세로 방향으로 반으로 가릅니다. */
```

> #### 🍒 MÉMO
> BulgogiCooking과 KimchiCooking의 `slice()`와 `cook()`은 각 메소드의 동작에서 차이가 존재한다.
