## 🫒 Routing Pages

### Using `pages` directory

Next.js에서 페이지는 **pages 폴더** 내부에 있는 React.js 컴포넌트를 추출한 것이다.

페이지의 라우팅 경로는 각 폴더 및 파일의 이름에 따라 결정된다.

![pages](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbKTNUo%2Fbtsdxi2vqVr%2FkvduebEroe8kLSkIHs83Z1%2Fimg.png)
pages 폴더를 이용한 라우팅

> #### 🍒MÉMO
> /authors/me 라는 새로운 경로를 추가하고 싶다면 폴더를 포함한 파일의 이름은 어떻게 되어야 할까?  
> A. authors/me.js  
> **B. pages/authors/me.js**  
> C. routes/authors/me.js

### Using `page.js` file

Next.js 13버전 부터는 라우팅을 할 때 pages 폴더를 이용한 방식과 다른 방식을 추가로 제공한다.

**page.js 파일**은 라우트를 제공하는 UI로 해당 파일의 컴포넌트를 추출함으로써 페이지를 정의할 수 있다.

중첩된 폴더에 page.js를 만들어 다양한 경로를 생성 가능하다.

> #### 🍒 MÉMO
> page.js 파일은 app 폴더 하위에서 작성해야 한다.

![page.js](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbTdgPx%2FbtsdGcAh3ON%2FSaU8rz6LaZPuN0AjKJyIAK%2Fimg.png)
page.js 파일을 이용한 라우팅

> #### 🐰 RÉFÉRENCE
> [Next.js 공식 문서 - Pages in Next.js](https://nextjs.org/learn/basics/navigate-between-pages/pages-in-nextjs "Next.js 공식 문서 - Pages in Next.js")  
> [Next.js beta 문서 - Pages](https://beta.nextjs.org/docs/routing/pages-and-layouts#pages "Next.js beta 문서 - Pages")
