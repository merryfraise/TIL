## 🐳 Conditional Rendering

### 메인 프로젝트 보강

지난 2월 공식적으로 코드스테이츠의 메인 프로젝트가 종료된 후, 팀원들끼리 추가할 기능을 더 추가하자고 회의하였는데 그 중 내가 맡은 화면은 이메일 인증 화면....

<div align="center">

  ![이메일 인증 화면 figma](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FdElGCQ%2Fbtsk8i7TBm6%2FStj8dy4Eb8NlvQJsKIUTqk%2Fimg.png)

  이메일 인증 화면 figma

</div>

화면 정의서를 보고 생각한 것은, 조건부 렌더링을 이용해야겠다는 것이었다. 인증코드 발급 버튼을 누른 전 후로 이메일 입력 창에 값을 넣을 수 없게 비활성화 되면서 버튼 아래에 인증코드 입력 창이 뜨기 때문이다.

### 컴포넌트 나누기

우선적으로 해야할 일은 컴포넌트를 나누는 것이다. Styled-Components를 이용하여 이메일 입력 컴포넌트(`EmailInput`)와 인증번호 입력 컴포넌트(`VerifyInput`)로 나누었다.

```jsx
const EmailInput = styled.div``;
const VerifyInput = styled.div``;

const Email = () => {
  return (
    <>
      <EmailInput />
      <VerifyInput />
    </>
  )
};
```

여기서 `VerifyInput` 컴포넌트가 인증번호 발급 버튼을 누른 후 렌더링 되어야하는 컴포넌트이다.

### 조건부 렌더링

골격을 전부 짰다면 기능을 넣을 차례이다. 인증코드 발급 버튼을 누른 뒤 일어나야 하는 변화는 2가지이다.

1.  `EmailInput` 컴포넌트의 `input` 창 입력을 막기
2.  `VerifyInput` 컴포넌트가 렌더링 되기

여기서 인증코드 발급 버튼이 눌린 것을 감지하기 위해서 상태값이 필요하다고 생각이 되었기 때문에 `const [isSend, setIsSend] = useState({ send: false });` 라는 코드를 삽입해주었다.  
`isSend`의 값은 버튼이 눌렸다면 `{ send: true }`로 변경해줄 것이다. 초기값은 눌러준 상태가 아니기 때문에 `false`로 설정해주었다.

```jsx
const EmailInput = styled.div``;
const VerifyInput = styled.div``;

const Email = () => {
  const [isSend, setIsSend] = useState({ send: false });
  
  return (
    <>
      <EmailInput />
      <VerifyInput />
    </>
  )
};
```

#### `EmailInput` 컴포넌트의 `input` 창 입력을 막기

`input`의 입력을 막는 것은 2가지 방법이 있다.

-   `disabled` 속성 이용
-   `readonly` 속성 이용

여기서 `disabled` 속성은 `input`에 입력된 내용을 `form`으로 보내주지 않는다. 반면 `readonly` 속성은 입력을 막지만 `input`에 입력된 내용을 `form`으로 전송해준다.

```html
<input type="text" value="read only" readonly />
<input type="text" value="disabled" disabled />
```

이 때, 내가 원하는 것은 버튼을 클릭했을 때 `readonly` 속성을 추가해주는 것이기 때문에 아래와 같이 코드를 작성해주었다.

```jsx
const EmailInput = styled.div``;
const VerifyInput = styled.div``;

const Email = () => {
  const [isSend, setIsSend] = useState({ send: false });
  
  const handleSend = () => {
    setIsSend({ ...isSend, send: true });
  }
  
  return (
    <>
      <EmailInput>
        <input readOnly={isSend.send ? true : false} />
        <button onClick={handleSend}>인증코드 발급</button>
      </EmailInput>
      <VerifyInput />
    </>
  )
};
```

#### `VerifyInput` 컴포넌트가 렌더링 되기

`VerifyInput` 컴포넌트 또한 `isSend`의 값이 `true`가 되면 렌더링 되어야 한다.

따라서 다음과 같이 코드를 작성하였다.

```jsx
const EmailInput = styled.div``;
const VerifyInput = styled.div``;

const Email = () => {
  const [isSend, setIsSend] = useState({ send: false });
  
  const handleSend = () => {
    setIsSend({ ...isSend, send: true });
  }
  
  return (
    <>
      <EmailInput>
        <input readOnly={isSend.send ? true : false} />
        <button onClick={handleSend}>인증코드 발급</button>
      </EmailInput>
      {isSend.send && <VerifyInput />}
    </>
  )
};
```

### 결과 화면 및 느낀점

<div align="center">

  ![이메일 유효성 검사 1](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fochxu%2Fbtsk80e0ytn%2FK60o0kCEeXZZTRk8SC6eS1%2Fimg.png)

  이메일 유효성 검사 1

  ![이메일 유효성 검사2](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FIVi8A%2Fbtsk84n4a5G%2F5oKjWILzC3im2ypPyTRws1%2Fimg.png)
  
  이메일 유효성 검사2

  ![조건부 렌더링](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fdall0E%2FbtslaHSUiVq%2FmOfB5pdLanEBQnddsimUp0%2Fimg.png)

  조건부 렌더링

</div>

코드를 작성하면서 기존에 습득했던 지식이 많이 휘발되었음을 느꼈다. 특히 버튼 클릭을 통한 조건부 렌더링을 구현하면서 `onClick` 속성을 `onChange`로 작성하여 렌더링 되지 않는 문제를 저질렀음을 보고 많이 느끼게 되었다...🥲

이 포스트에 작성한 코드가 실제 작성한 코드의 전부는 아니지만 특히 `input`에 `readonly`와 같은 속성을 추가하는 경우 미래의 나에게 도움이 되리라 믿고..! (처음에는 HTML에서 그냥 `readonly`만 넣는 속성을 React.js로 어떻게 작성해야 할 것인지 고민이 컸는데 `true`, `false`만 지정해주면 되는 문제였다 😅)

결론! 다른 지식 습득하겠다고 가장 중요한 것을 놓치지 말아야겠다는 생각이 많이 들었다..!!
