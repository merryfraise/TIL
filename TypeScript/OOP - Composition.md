## 🫐 OOP - Composition

### Composition

Inheritance의 의존성 문제를 해결하기 위한 방법이다.

<div align="center">
  
  ![Inheritance](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbEtCDM%2FbtsdZAaOBnG%2FoLh6BbiabqOMtNJaDl4JkK%2Fimg.png)
  
  Inheritance
  
</div>

위의 그림에서는 Bulgogi Cooking과 Kimchi Cooking이 Cooking과의 관계에서 한 단계의 상속 관계를 가지지만, Bulgogi Cooking에서 Soy Bulgogi나 Seasoned Bulgogi등이 상속되거나 Bulgogi Cooking이나 Kimchi Cooking을 합쳐서 Kimchi Bulgogi를 만들고자 한다면 상속이 문제점이 될 수 있다.

<div align="center">
  
  ![Inheritance 문제점](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcqHYmy%2Fbtsd0tvbAKV%2FFtZPmek4sqqZsai6wvlKi1%2Fimg.png)
  
  Inheritance의 문제점
  
</div>

이런 경우 Cooking과 그 하위 객체들의 관계가 너무 밀접하게 연결되어 있어 의존도가 높고, Kimchi Bulgogi의 경우 Bulgogi Cooking과 Kimchi Cooking을 동시에 상속할 수 없기 때문에 이를 해결하기 위해 Composition이란 방법을 사용한다.

Composition은 조합, 합성이라는 뜻으로, Cooking에 필요한 정보들을 다른 객체로 만들어두고 이를 조합하여 새로운 클래스를 만들어내는 방법이다.

<div align="center">
  
  ![Composition](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2F2XfzT%2FbtsdZNudh9m%2Fk26Fg7EXKuAWczTHH1Knr1%2Fimg.png)
  
  Composition
  
</div>

### Example

```ts
// 양념 클래스
interface Seasoning {}

class Soy implements Seasoning {}
class Pepper implements Seasoning {}
class White implements Seasoning {}

// 요리 클래스
interface Cook {}

class Cooking implements Cook {
  constructor(
    _,
    private seasoning: Seasoning
  ) {}
}

// 양념 인스턴스
const soy = new Soy();
const pepper = new Pepper();
const white = new White();

// constructor에 따라 다양한 요리 인스턴스 생성 가능
const soyBulgogi = new Cooking(_, soy);
const pepperBulgogi = new Cooking(_, pepper);

const redKimchi = new Cooking(_, pepper);
const whiteKimchi = new Cooking(_, white);
```
