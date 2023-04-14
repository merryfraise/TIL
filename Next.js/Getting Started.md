## 🫒 Getting Started

### Next.js 설치

설치 전 요구사항!

> #### 🍒 MÉMO
> Node.js 14.6.0 이상 버전 (공식 문서 기준)  
> Node.js 16.8.0 이상 버전 (beta 문서 기준)

#### **Node.js 업데이트 하기**

14.6.0 버전 이상의 Node.js를 요구하기 때문에 일단 현재 Node.js의 버전을 알 필요가 있다.

```bash
node -v
```

![node -v](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbRbOe6%2Fbtr9zNLqHbO%2F3IDEAI7ccpv07LPSNaz8Hk%2Fimg.png)
나의 Node.js 버전은 19.8.1이기 때문에 조건 충족!

만약 그 이전 버전의 Node.js 환경이라면 다음 방법으로 Node.js를 업데이트 할 수 있다.

우선 npm의 캐시를 비워주어야한다.

```bash
npm cache clean -f
npm cache verify
```

> #### 🍒 MÉMO
> `npm cache clean -f`는 모든 캐시를 없애는 명령어이고 `npm cache verify`는 캐시 폴더의 내용을 확인한 뒤 꼬인 부분을 체크하고 해결하는 명령어이다.  
> 전자는 모든 캐시를 완전히 삭제해버리기 때문에 보통 후자를 추천한다고 한다.

npm 캐시를 비워주었다면 Node.js 버전 관리 플러그인 n을 설치한다.

```bash
npm install -g n
```

n을 설치했다면 명령어를 이용해 버전 업데이트를 해준다.

작성일 기준 최신 lts 버전은 18.15.0, 최신 버전은 19.9.0이다.

```bash
n lts # 최신 lts 버전
n latest # 최신 버전
```

> #### 🍒 MÉMO
> 최신 버전보다는 lts가 안정적이기 때문에 `n lts`를 추천하는데 어째서인지 내 맥북에는 최신 버전에 가까운 버전이 깔려있다..^^

#### **설치하기**

```bash
npx create-next-app@latest # 공식 문서 버전
npx create-next-app@latest --experimental-app # beta 버전
```

두 명령어에 큰 차이가 무엇이 있을지 직접 실행해 보았다.

![npx create-next-app@latest](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbiSOE9%2Fbtr9AatfYon%2FKhBAabj889R274kuxodja1%2Fimg.png)
npx create-next-app@latest
![npx create-next-app@latest --experimental-app](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2F8Gihc%2Fbtr9BY6Dso2%2FmAJklFutiTpK1zkkiFQ9LK%2Fimg.png)
npx create-next-app@latest --experimental-app

큰 차이가 없어보인다!

package.json도 살펴보았는데 dependecies에 설치된 목록과 버전이 모두 동일했다.

+) 2023.04.14 추가

```bash
npx create-next-app@latest --experimental-app
```

위 명령어는 최신 버전의 Next.js를 설치하면서, 실험적인 기능을 사용할 수 있는 프로젝트를 생성하는 방법이다. (`--experimental-app`)

> #### 🐰 RÉFÉRENCE
> [Next.js 공식 문서](https://nextjs.org/docs "Next.js 공식 문서")  
> [Next.js beta 문서](https://beta.nextjs.org/docs/installation "Next.js beta 문서")  
> [npm cache 해결](https://icerabbit.tistory.com/78 "npm cache 해결")
