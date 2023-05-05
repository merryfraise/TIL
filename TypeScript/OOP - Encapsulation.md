## 🫐 OOP - Encapsulation

### Encapsulation

캡슐화는 서로 연관된 데이터를 하나의 캡슐로 묶어두는 것을 의미한다고 저번 포스팅에 작성해두었다.

<div align="center">
  
  ![Encapsulation](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbVAYHB%2Fbtr92pCeqHn%2FuwVaGbF6iakgYx8xzfv4UK%2Fimg.png)

  Encapsulation
  
</div>

이렇게 캡슐화를 하는 것에는 크게 2가지 이유가 존재한다.

- 데이터 보호 (data protection) - 클래스 내부에 정의된 데이터를 외부로부터 보호
- 데이터 은닉 (data hiding) - 내부의 동작을 감추고 필요한 부분만 외부에 노출

이 중 데이터 은닉을 실현하기 위해 쓸 수 있는 것이 바로 **access modifier**이다.

### Access modifier

Access modifier는 데이터에 대한 접근(access)을 제어(modify)하는 것으로, `public`, `private`, `protected`가 존재한다.

| access modifier | 클래스 내부 | 자식 클래스 | 인스턴스 | 설명 |
| --- | --- | --- | --- | --- |
| `public` (default) | ⭕️ | ⭕️ | ⭕️ | 모든 곳에서 접근 가능 |
| `private` | ⭕️ | ❌ | ❌ | 자신 내부에서만 접근 가능 |
| `protected` | ⭕️ | ⭕️ | ❌ | 인스턴스에서 접근 불가능 |

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

  slice(): void {
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

  boil(): void {
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
}

const ramyeon = new Cooking({
  봉지라면: { sliceable: false, boilable: true },
  버섯: { sliceable: true, boilable: true },
  콩나물: { sliceable: false, boilable: true },
});

ramyeon.slice();
/* 버섯 재료를 썹니다. */

ramyeon.boil();
/* 봉지라면 재료를 끓입니다.
   버섯 재료를 끓입니다.
   콩나물 재료를 끓입니다. */
```

> 🐰 RÉFÉRENCE
> 
> [객체 지향 프로그래밍의 4가지 특징ㅣ추상화, 상속, 다형성, 캡슐화](https://www.codestates.com/blog/content/%EA%B0%9D%EC%B2%B4-%EC%A7%80%ED%96%A5-%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D-%ED%8A%B9%EC%A7%95 "객체 지향 프로그래밍의 4가지 특징ㅣ추상화, 상속, 다형성, 캡슐화")
