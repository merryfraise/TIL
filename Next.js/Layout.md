## 🫒 Layout

### Layout

layout.js는 공통된 UI를 제공하는 컴포넌트이다.

layout.js에 화면에서 공통적으로 보여줄 화면을 미리 작성해두고, 그 외 개별 페이지에서 다르게 보여줄 화면은 `children`으로 전달하는 식

```ts
/* app/dashboard/layout.tsx */
export default function DashboardLayout({
  children, // will be a page or nested layout
}: {
  children: React.ReactNode;
}) {
  return (
    <section>
      {/* Include shared UI here e.g. a header or sidebar */}
      <nav></nav>
      {children}
    </section>
  );
}
```

/dashboard url 아래에 있는 페이지들에서는 `nav`를 모두 표시해주고 그 아래 개별 페이지에 따른 화면이 그려질 것이다.

### RootLayout

app 폴더 안에는 꼭 하나 이상의 layout.js 파일(RootLayout 컴포넌트)이 존재해야만 한다.

RootLayout 컴포넌트는 서버로부터 반환된 초기 HTML을 수정하는 역할을 한다.

```ts
/* app/layout.tsx */
export default function RootLayout({
  children,
}: {
  children: React.ReactNode,
}) {
  return (
    <html lang="en">
      <body>{children}</body>
    </html>
  );
}
```

### Nesting Layouts

위의 두 가지 예제 코드를 보면 app 폴더 내부에 layout.js 파일이 존재해야만 하고, 각 엔드포인트에 따른 layout.js 파일 또한 존재할 수도 있다.

이 경우 RootLayout 컴포넌트가 하위 Layout 컴포넌트를 감싸는 형태로 레이아웃의 중첩이 일어난다.

<div align="center">
  
  ![Nesting Layouts](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fbl9cLU%2FbtseqY9QqSw%2FyrJbbiQERBfCvOUruxM8oK%2Fimg.png)
  
  Nesting Layouts
  
</div>

그림은 app/layout.js의 `children` 내부에 app/dashboard/layout.js가 위치하게 되는 모습을 보여준다.

> #### 🐰 RÉFÉRENCE
> [Next.js 공식 문서 - Layouts](https://nextjs.org/docs/app/building-your-application/routing/pages-and-layouts#layouts "Next.js 공식 문서 - Layouts")
