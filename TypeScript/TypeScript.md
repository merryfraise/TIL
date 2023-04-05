<h2 style="border: 1px solid #d4d4d4; border-left-color: #C8BEE4; display: inline-block; padding: 7px 40px 7px 15px; border-left-width: 23px; background-size: 10px, 30px, 10px 10px, 30px 30px; background-image: linear-gradient(90deg, #f2f2f2 1px, transparent 1px), linear-gradient(90deg, #f2f2f2 1px, transparent 1px), linear-gradient(#f2f2f2 1px, transparent 1px), linear-gradient(#f2f2f2 1px, transparent 1px); font-weight: bold;" data-ke-size="size26">🫐 TypeScript 맛보기 😋</h2>
<h3 style="font-weight: bold;" data-ke-size="size23">TypeScript가 뭔데?!</h3>
<p data-ke-size="size16">TypeScript는 JavaScript를 기반으로 <span style="color: #0593d3;"><b>정적 타입 문법을 추가</b></span>한 언어이다.</p>
<p data-ke-size="size16">JavaScript는 런타임 시에 타입이 결정되는 동적인 특징을 갖고 있는데, 이를 컴파일타임 시에 타입이 지정되도록 정적으로 변환한 것이 바로 TypeScript이다.</p>
<pre id="code_1680702588149" class="javascript" data-ke-language="javascript" data-ke-type="codeblock"><code>let name = 'Shoupeach';
name = true;

/* 런타임시에 타입이 결정되기 때문에
string에서 boolean으로 변경해도 문제가 없다! */</code></pre>
<pre id="code_1680702693231" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>let name: string = 'Shoupeach';
name = true; // 🚨 error occurred 🚨

/* 컴파일시에 타입이 결정되기 때문에
string에서 boolean으로 변경할 시 에러가 발생한다 ㅠㅠ */</code></pre>
<p data-ke-size="size16">&nbsp;</p>
<h3 style="font-weight: bold;" data-ke-size="size23">TypeScript 설치하기</h3>
<p data-ke-size="size16">현재 진행중인 프로젝트에만 설치하고 싶다면</p>
<pre id="code_1680703423214" class="bash" data-ke-language="bash" data-ke-type="codeblock"><code># using npm
npm install typescript --save-dev

# using yarn
yarn add typescript --dev</code></pre>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">전역적으로 설치하고 싶다면</p>
<pre id="code_1680703452214" class="bash" data-ke-language="bash" data-ke-type="codeblock"><code># using npm
npm install typescript -g

# using yarn
yarn global add typescript</code></pre>
<p data-ke-size="size16">&nbsp;</p>
<h3 style="font-weight: bold;" data-ke-size="size23">tsc 기초 명령어</h3>
<p data-ke-size="size16">TypeScript 설치를 마쳤다면 <code>tsc</code> 명령어를 사용할 수 있다!</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16"><code>tsc</code>를 이용한 명령어 목록을 확인하기</p>
<pre id="code_1680703863855" class="bash" data-ke-language="bash" data-ke-type="codeblock"><code>tsc -h
tsc --help</code></pre>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">TypeScript의 버전 확인하기</p>
<pre id="code_1680703923557" class="bash" data-ke-language="bash" data-ke-type="codeblock"><code>tsc -v
tsc --version</code></pre>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">ts 파일을 js 파일로 컴파일하기</p>
<pre id="code_1680704024040" class="bash" data-ke-language="bash" data-ke-type="codeblock"><code>tsc file-name.ts</code></pre>
<p>[##_Image|kage@cjytN0/btr8hs9ARQA/ZrKw5IqhYeUp1I4XYZMazk/img.png|CDM|1.3|{"originWidth":996,"originHeight":120,"style":"alignCenter","caption":"tsc file-name.ts 사용시 주의사항!!","filename":"스크린샷 2023-04-05 오후 11.15.47.png"}_##]</p>
<blockquote data-ke-style="style2"><br /><code>tsc file-name.ts</code>으로 컴파일을 할 경우 tsconfig.json의 설정을 무시하고 기본 컴파일 옵션으로 컴파일된다.<br />(Ignoring tsconfig.json, compiles the specified files with default compiler options.)</blockquote>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">자동 컴파일하기</p>
<pre id="code_1680704248736" class="bash" data-ke-language="bash" data-ke-type="codeblock"><code>tsc -w
tsc --watch</code></pre>
<blockquote data-ke-style="style2"><br />작성한 ts 파일에 변화가 있을 때마다 tsc file-name.ts를 실행해야 컴파일 된 js 파일에도 변화가 적용된다.<br />이 때, <code>tsc -w</code>를 사용해 watch mode를 작동시키면 ts 파일에 변화가 감지될 때마다 자동으로 js 파일로 컴파일을 한다.</blockquote>
<p data-ke-size="size16">&nbsp;</p>
<blockquote data-ke-style="style3"><br /><a title="TypeScript 공식 문서" href="https://www.typescriptlang.org/" target="_blank" rel="noopener">TypeScript 공식 문서</a></blockquote>
