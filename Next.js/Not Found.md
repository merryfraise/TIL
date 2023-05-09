## 🫒 Not Found

### Not Found

not-found.js는 Next.js에서 제공해주는 404 전용 페이지이다.

Next.js 13 이전 버전에서는 `notFound()`를 page.js에 삽입하여 404 응답을 캐치했을 때 `notFound()` 메소드가 not-found.js를 표시해주는 역할을 하였는데, 13 버전부터는 404로 응답이 돌아왔을 때 바로 not-found.js를 표시하도록 변경되었다.

not-found.js를 app 폴더 내에 넣어서 전체적인 404 페이지를 보여줄 수도 있고, 특정 엔드포인트에 해당하는 404 페이지만 보여줄 수도 있다.

```ts
/* app/blog/not-found.tsx */
export default function NotFound() {
  return (
    <>
      <h2>Not Found</h2>
      <p>Could not find requested resource</p>
    </>
  );
}
```

/blog url 하위에 있는 페이지에서는 위의 404 페이지가 보일 것이다.

> #### 🐰 RÉFÉRENCE
> [Next.js 공식 문서 - not-found.js](https://nextjs.org/docs/app/api-reference/file-conventions/not-found "Next.js 공식 문서 - not-found.js")
