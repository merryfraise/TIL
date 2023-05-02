## 🫒 Dynamic Routing

### Using `pages` directory

경로를 동적으로 관리하고자 하는 폴더 및 파일의 이름에 대괄호를 써준다.

![pages](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2F29Xsk%2FbtsdBOtzq9h%2FIpyjWBxut5HO0m3r6HOygK%2Fimg.png)
pages 폴더를 이용한 라우팅

### Using `page.js` file

경로를 동적으로 관리하고자 하는 폴더의 이름에 대괄호를 써준다.

이 때 폴더 명은 일반적으로 `[slug]`나 `[id]`를 사용한다.

![page.js](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbKtwF2%2FbtsdIHM90Kq%2FQaeWedWsizHxVP0TJskJj0%2Fimg.png)
page.js 파일을 이용한 라우팅

> #### 🍒 MÉMO
> pages 폴더 이용방식이나 page.js 파일 이용방식이나 모두 `[...slug]`를 사용했을 때, /:slug 이하의 모든 경로를 동적으로 관리 가능하다.  
> /:slug 상단의 경로도 동적으로 관리할 때는 `[[...slug]]`를 사용할 수 있다.

> #### 🐰 RÉFÉRENCE
> [Next.js 공식 문서 - Page Path Depends on External Data](https://nextjs.org/learn/basics/dynamic-routes/page-path-external-data "Next.js 공식 문서 - Page Path Depends on External Data")  
> [Next.js beta 문서 - Dynamic Segments](https://beta.nextjs.org/docs/routing/defining-routes#dynamic-segments "Next.js beta 문서 - Dynamic Segments")
