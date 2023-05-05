## 🫒 Next.js

### Next.js란?

Next.js는 웹 애플리케이션을 만들 때 사용하는 React.js 프레임워크이다.

<div align="center">

  ![Next.js](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbXLsSG%2Fbtr8KKnX7fM%2FHV3HNPmtK9mdJPFCB2Crzk%2Fimg.png)
  
</div>

React.js로 UI를 만들면서, CSR과 SSR/SSG, 라우팅, 데이터 페칭 등을 한꺼번에 할 수 있게 해주는 종합선물세트 같은 역할을 한다.

React.js만으로도 third party library를 함께 사용해 웹 애플리케이션을 만들 수 있는데, 그럼 왜 Next.js를 사용하는 걸까? 🧐

이 때 빠지지 않는 이야기가 바로 **CSR vs SSR**에 대한 이야기인 것 같다...

<div align="center">

  <img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fqq4o4%2Fbtr8LOpUROE%2FhuEKAvDOGxWpQIzJatpw01%2Fimg.jpg" width="320" />

  csr과 ssr의 이야기를 향해...
  
</div>

### CSR vs SSR 그리고...

간단히 말하자면 React.js는 CSR을 지원하는데 Next.js는 SSR도 지원한다..

> #### 🍒 MÉMO
> React.js로도 SSR 구현이 가능하지만 추가 라이브러리와 여러 설정이 필요하기 때문에 Next.js를 사용하는 것이 훨씬 간단 👍🏻

#### **CSR**

CSR은 **C**lient **S**ide **R**endering의 약자로 클라이언트에서 페이지를 렌더링하는 방식을 말한다.

CSR의 보완을 위해 SSR, SSG, ISR등의 방식이 생겼는데 후술할 3가지의 방식과 ❗️완전히 반대편에 있는❗️ 방식이다.

<div align="center">

  ![CSR](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2F0XBl6%2Fbtr8LhTsIBU%2FAtEjSXvjvkpN8HOKDa3d41%2Fimg.jpg)

  CSR 작동 방식
  
</div>

사이트에 접속하면 빈 HTML을 보여주며 JavaScript 파일을 다운받아 빈 HTML에 DOM을 생성해서 렌더링한다.

초기 페이지 로딩까지의 시간이 길고 이후에는 렌더링이 필요한 위치만 부분적으로 렌더링이 이루어지기 때문에 속도가 빠르다.

그리고 렌더링이 클라이언트에서 이루어지기 때문에 서버에 걸리는 부하가 적다는 것이 장점이다.

하지만 초기 페이지 로딩의 시간동안 화면에 렌더링되는 정보가 아무것도 없기 때문에 SEO에 불리하다.

#### **SSR**

검색 엔진에 최적화하기 위한 방식으로 **S**erver **S**ide **R**endering의 줄임말이다.

<div align="center">

  ![SSR](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbQVCOI%2Fbtr8NcYfgo2%2FhR2T9gYwegGilR78WAzrM1%2Fimg.jpg)

  SSR 작동 방식
  
</div>
  
CSR과 달리 서버에서 유저에게 보여줄 페이지를 HTML로 만들어 요청하는 정보만 렌더링하게 된다.

만들어진 HTML을 서버로부터 받기 때문에 SEO에 유리한 것이 장점이다.

SEO에는 좋지만... 매 요청마다 HTML을 서버로부터 받아와야하기 때문에 서버에 부하가 많이 걸린다.

#### **SSG**

SSR이 장점만 가진 것이 아니기 때문에 서버에 부하를 줄이기 위한 방법들도 존재한다.

SSG가 그 중 하나로, **S**tatic **S**ite **G**eneration의 줄임말이다.

<div align="center">

  ![SSG](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FsmQvP%2Fbtr8LOp38In%2F9IhsrOtmK0PgE8IK9VQBDK%2Fimg.jpg)
  
  SSG 작동 방식
  
</div>

SSG도 서버가 HTML을 만들어 렌더링을 하지만, 렌더링하는 시점이 SSR과 다르다.

파일을 빌드하는 시점에 렌더링을 하여 화면에 보여주기 때문에 데이터를 실시간으로 주고받을 수 없다.

#### **ISR**

SSG를 보완하기 위한 방법으로 **I**ncremental **S**tatic **R**egeneration의 줄임말이다.

<div align="center">

  ![ISR](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbvRM7u%2Fbtr8KI4VwYF%2F1KoljpkkaCW8AbxP84c9uk%2Fimg.jpg)
  
  ISR 작동 방식
  
</div>

기본 작동 방식은 SSG와 동일하지만 ISR은 주기적으로 렌더링을 다시 한다는 점에서 차이가 있다.

하지만 `'주기적' = '요청시'`가 아니기 때문에 ISR 또한 실시간으로 데이터를 주고 받을 수 없다.

### 그래서 결론은?! 🤔

CSR로 시작해 ISR로 끝난 렌더링 방법에서 볼 수 있듯이, CSR / SSR / SSG / ISR 모두 완벽한 방법이 아니고 모두 단점이 존재한다..😅

장단점이 분명하기 때문에 취사선택해서 쓸 수밖에 없는데, [Next.js는 위의 렌더링 방식들을 지원](https://nextjs.org/learn/foundations/how-nextjs-works/rendering "Next.js 공식 문서 - 렌더링")한다!!

심지어 짬뽕🍜해서 사용도 가능하니 왜 Next.js를 사용해야 하는지에 대한 충분한 답이 되지 않을까?

<div align="center">

  ![비교](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fch14Xg%2Fbtr8LLz4lyK%2FudB0opqO3ogAFWKgikKyK0%2Fimg.png)
  
  렌더링 방식에 따른 장/단점 비교
  
</div>

> #### 🐰 RÉFÉRENCE
> 
> [Next.js 공식 문서](https://nextjs.org/learn/foundations/about-nextjs/what-is-nextjs "Next.js 공식 문서")  
> [CSR, SSR, SSG, ISR](https://dev.to/pahanperera/visual-explanation-and-comparison-of-csr-ssr-ssg-and-isr-34ea "CSR, SSR, SSG, ISR")
