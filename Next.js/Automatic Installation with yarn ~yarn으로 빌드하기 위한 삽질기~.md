## 🫒 Automatic Installation with yarn (yarn으로 빌드하기 위한 삽질기)

### 1달 가까이 Next.js를 멀리하면서...

그 동안 알고리즘 공부, TypeScript 공부 등등으로 바쁘기도 했지만, Next.js로 프로젝트를 생성한 뒤 `yarn`으로 빌드를 하면 자꾸만 패키지를 찾을 수 없다는 등의 오류로 멀리하게 되었다. (웃긴 점은 해당 오류는 IDE 화면에서만 뜨고 컴파일 및 빌드는 작동되긴 함... 하지만 빨간 줄이 너무 많아서 보고 싶지 않았음 🥹)

그러다가 이제 진짜 사이드 프로젝트 돌입을 하게 될 것 같아서 Next.js와 다시 친해져보고자 기존에 생성해뒀던 프로젝트를 지우고 처음부터 다시 시작해보자! 라는 거창한 생각으로 다시 터미널을 켜게 되었다.

<div align="center">

  ![그 땐 몰랐었지..](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FdEhhrF%2FbtskS5nZRBR%2FtCZoMaH6jwFkYdfHrUEOOk%2Fimg.jpg)

  그 땐 몰랐었지..

</div>

그 땐 몰랐다... 이 오류를 해결하기 위해 무려 하루 하고도 2시간을 더 할애하게 될 줄은...

### 시작은 달콤하게 평범하게 공식문서에 끌려

New 프로젝트를 생성하기 이전, 내가 생각한 기존 프로젝트의 문제점은 공식문서를 그대로 따라 설치를 한 것이 아니라는 점이다.

`yarn`을 사용하고 싶었기 때문에 설치 명령어 또한 `yarn`으로 진행했는데, 공식문서에서 제공하는 명령어는 다음과 같다. (참고로 내가 기존 프로젝트를 설치했을 때는 beta 문서 버전의 명령어를 사용했다... 5월 기준으로 beta 문서가 현재 공식문서가 됨)

```bash
npx create-next-app@latest
```

나의 경우 `npx`를 `yarn`으로 변경하여 설치했었다는 뜻..!! ^^ 참고로 `yarn`을 사용한 명령어는 문서에서 제공하고 있지 않기 때문에 이것이 문제라고 생각하고 이번에는 공식문서를 따라 그대로 설치를 진행하였다. (참고로 삽질 하면서 이번에도 `yarn create-next-app@latest`를 해보았는데 안되더라..? 그 땐 왜 됐던 거지 🤔)

설치를 무사히 마치고 바로 `yarn dev`를 작성해준 결과는?

<div align="center">

  ![yarn install 해봐~^^](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbolkPx%2FbtskSSPUZRZ%2FYwkMySrVT3OaymKcQJVUnk%2Fimg.png)

  yarn install 해봐~^^

</div>

내가 봤던 다른 영상에선 바로 `yarn dev`해도 되던데 왜 나는 안돼...? 제대로 작동할 것이란 기대를 부수고 에러를 내뱉었다...🥹

run "yarn install" to update the lockfile이라고 하니.. 아마 yarn.lock 파일이 없어서 그런 것 같아 적혀있는 대로 yarn install을 해준 결과, 다시 마주하게 되는 수 많은 빨간 줄들 (지인의 사진을 훔쳐왔다)

<div align="center">

  ![안녕하세요!](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2F7YHvK%2FbtskY7EClK1%2F8R03F1KJOZfFpdOVL3Kvkk%2Fimg.png)

  안녕하세요!

</div>

대충 나도 이런 모습을 보여주고 있었다는 뜻.. 그럼 `npx`가 아닌 `yarn`으로 설치했던게 문제는 아니라는 것 같은데 대체 무엇이 문제인걸까 🥹

### Node 버전을 변경해볼까?

내 맥북에 깔려있는 node의 버전은 19.7.1이었다. 현재 lts 버전은 그보다 낮은 18버전이다.

이전에 Next.js 설치 블로깅을 하면서 node 버전에 관해서 작성해둔 것이 있었는데, lts 설치를 했음에도 불구하고 내 node 버전은 19버전이었다!! => [🫒 Getting Started](https://github.com/merryfraise/TIL/blob/main/Next.js/Getting%20Started.md) (node 버전 변경 관련 내용 보러가기)

안정성이 떨어지는 버전이라 문제가 있는 것인가 싶어 다시 node 버전을 변경하는 것을 도전하였다.

결론부터 말하자면 위의 블로깅에 적혀있는 방법은 먹히지 않았는데 이유는 active한 버전은 `brew`로 설치한 것이었고, 그 외 꾸준히 lts를 설치해왔던 버전들은 `n`으로 설치한 것이었기 때문 ㅎㅎ ㅋㅋㅋㅋㅋㅋ

<div align="center">

  ![과거의 나는 무슨 짓을 한 것일까](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FckkE8M%2FbtskTJkVuBq%2F6T2tK7BPQuKujL0jxyOJnk%2Fimg.jpg)

  과거의 나는 무슨 짓을 한 것일까

</div>

최신 버전으로 설치된 `brew` node를 삭제하려고 했는데 (n으로는 lts를 잘 설치해뒀기 때문...), 잘못 건드리면 돌아오지 못할 강을 건너게 될 것 같아서 `brew`로 node를 lts 버전으로 변경하기로 노선을 돌렸다... (다행히) 방법은 어렵지 않다.

#### **현재 설치된 버전 찾기**

```bash
brew search node
```

현재 설치된 버전의 node를 찾아주는 명령어이다. 설치되어 있는 노드는 `node@12`, `node@13`, ..., `node@18`, `node` 등으로 표기 되는데 나의 경우 `node`가 설치되어있었다. 아마 이게 최신 버전의 node인 듯하다.

#### **원하는 버전 설치하기**

```bash
brew install node@18
```

내가 원하는 것은 lts 버전을 설치하는 것이기 때문에 현재 lts 버전에 속한 `node@18`을 설치하면 자동적으로 lts 버전을 설치해준다.

#### **현재 버전 해제하기**

```bash
brew unlink node
```

그리고 최신 버전인 `node`와의 연결을 끊어버린다.....

#### **원하는 버전 연결하기**

```bash
brew link node@18
```

이후 `node@18`과 연결 해주면 되는데... 되는데..!! 오류가 발생했다. 이미 심볼릭 링크가 존재하기 때문에 발생하는 오류인데, 심볼릭 링크를 삭제한 뒤 다시 위의 명령어를 입력해주면 된다.

#### **심볼릭 링크 삭제하기**

```bash
rm '/opt/homebrew/bin/npm' '/opt/homebrew/bin/npx'
rm -rf '/opt/homebrew/lib/node_modules/npm'
```

심볼릭 링크 삭제 명령어

<div align="center">

  ![버전 변경에 성공하다 🥹](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcAhgIk%2FbtskS2kAmGB%2FvdsqZWxmQV5fdR0j9j1GE0%2Fimg.png)

  버전 변경에 성공하다 🥹

</div>

위의 과정을 거쳐 드디어 lts 버전으로 node 버전을 변경하는데 성공하였다. 그럼 프로젝트에서도 오류가 일어나지 않겠지?

### npm과 yarn의 충돌 (yarn berry로 zero install 설정하기)

그런 일은 없었다.... 좀 더 근본적인 문제가 있는 것으로 보였다. 정말 엄청난 폭풍 구글링 끝에 npm과 yarn의 혼용으로 인한 일인 것 같다는 결론에 다다랐고..

<div align="center">

  ![많이 검색한 나를 봐 아주 많아](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbhNJsb%2FbtskZY8wkVF%2FiuOR2wMeTJKRKqilR2eb80%2Fimg.png)

  많이 검색한 나를 봐 아주 많아

</div>

Next.js의 공식문서에서는 `npx`로만 Automatic Installation 하는 법을 제공하는데, 그럼 `yarn`의 사용은 포기해야하는 것인가 싶었다.

그러다가 처음 `yarn install` 명령어를 입력했을 때 프로젝트에서의 변화를 떠올려보니 node\_modules 폴더가 사라졌던 것을 떠올렸고, 해당 폴더를 무시하고 `npm`에서 `yarn`으로의 마이그레이션이 가능한지 검색해보았다. (node\_modules 폴더가 사라졌기 때문에 패키지들을 인식하지 못하는 것 같다는 느낌이 들었음)

아래에 작성되는 모든 내용은 [패키지 매니저 npm에서 yarn berry(zero install)로 바꾸기](https://ahnanne.tistory.com/94 "패키지 매니저 npm에서 yarn berry(zero install)로 바꾸기")를 참고하였다.

위 글 작성자 분은 nodeLinker에 "node\_modules"를 추가하는 작업을 진행하셨지만 나는 해당 부분 무시하고 진행하였다. (`yarn` 명령어 치는 순간 node\_modules 폴더가 사라지는 현상이 있기 때문 랜덤인지는 모르겠는데 총 3회 시도 중 1회만 node\_modules 폴더가 살아남아있었고, 나머지 2회는 전부 사라짐)

#### **yarn.lock 생성하기**

```bash
yarn
```

#### **패키지 매니저 yarn으로 변경하기**

```bash
yarn set version berry
```

`set version berry`를 해주는 것은 zero install을 사용하기 위함이다.

#### **nodeLinker에 zero install 정보 입력하기**

```yml
nodeLinker: 'pnp'
```

.yarnrc.yml에 위 내용을 추가한다.

#### **gitignore 정보 추가하기**

```bash
# yarn berry
.yarn/*
!.yarn/cache
!.yarn/patches
!.yarn/plugins
!.yarn/releases
!.yarn/sdks
!.yarn/versions
```

.gitignore에 위 내용을 추가한다.

#### **yarn으로 패키지들 설치하기**

```bash
yarn install
```

여기까지 진행하면 역시나 빨간줄이 뜨는데 핵심은 다음 과정이었던 것 같다.

#### **eslint, prettier, ts 정상 작동시키기**

VSCode extension인 ZipFS를 설치 한 뒤,

```bash
yarn dlx @yarnpkg/sdks vscode
```

를 입력해주고, TypeScript 버전을 workspace 버전으로 설치하면 끝! (자세한 내용은 참고한 블로그에 자세히 서술되어 있음)

<div align="center">

  ![드디어 오류 없는 화면 🥹](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FA5UtK%2Fbtsk1b7zmYy%2F5mNT5BwI9YbZC5mLnlS950%2Fimg.png)

  드디어 오류 없는 화면 🥹

</div>

그러면 드디어 이렇게 깨끗한 화면을 마주할 수 있다...

<div align="center">

  ![dev 실행도 성공적](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fmr9JK%2Fbtsk1y9vKX0%2FYrOJz0xNVeKyPGzxgOw1r1%2Fimg.png)

  dev 실행도 성공적

</div>

`yarn dev`도 멀쩡하게 잘 작동한다 🥹

결론은 `npx create-next-app`으로 시작했기 때문에 벌어진 일 같긴 한데 (사실 이것때문인지 아니면 그냥 ZipFS extension이 없어서였는지 확실하지 않지만 아무튼 ㅠㅠ) 일단 해결됐으니 마음이 편안하다....

다가올 프로젝트에도 문제 없이 `yarn`으로 빌드할 수 있게 되었다는 것에 의미를 두겠다 🥹

> #### 🐰 RÉFÉRENCE
> [Homebrew로 node 버전 바꾸기](https://hanarotg.tistory.com/47 "Homebrew로 node 버전 바꾸기")  
> [패키지 매니저 npm에서 yarn berry(zero install)로 바꾸기](https://ahnanne.tistory.com/94 "패키지 매니저 npm에서 yarn berry(zero install)로 바꾸기")
