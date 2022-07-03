---
emoji: ⚗️
title: 리액트_#1
date: '2022-06-30'
author: AsanHo
tags:
categories: react
---

## 리액트는 왜 개발되었는가

기술은 문제를 해결하기 위해 개발된다. 그리고 해결하기 위한 문제가 무엇인지 안다면, 그 기술을 더 잘 이해 할 수 있게된다. 리액트가 좋다고는 하지만 좋다는 말만듣고, 왜 이게 만들어졌는지 이해하지 못한채 학습을 시작하는 사람이 굉장히 많다. 때문에 우리는 학습시 바닐라 js와 리액트를 비교하며 학습을 하게 될 것이다.

> react는 웹사이트에 interactivity(상호작용)을 만들어준다.

이것이 리액트가 해결하는 바닐라 js의 문제이다.

## 바닐라 js VS 리액트

먼저, 바닐라 js에서, 버튼을 감지할때마다, 콘솔에 수를 나타내주는 프로그램을 입력해보자

```html
<body>
  <h1>Total Clicks : 0</h1>
  <button>hello world!</button>
  <script>
    const btn = document.body.querySelector('button');
    const h1 = document.body.querySelector('h1');
    let num = 0;
    function add() {
      num = num + 1;
      h1.innerText = `Total Clicks : ${num}`;
    }
    addEventListener('click', add);
  </script>
</body>
```

별거 아닌 프로그램이지만 코드의 양이 상당히 많다.
html작성 -> 태그변수화 -> 함수작성 -> 이벤트리스너 작성이다.

## 리액트 convert

이제 이 프로그램을 리액트로 만들어볼것이다. 기억해야될 것은, 리액트는 js에서만 작성하게 된다. html을 js와 **분리**하지 않는다. 또한 이 리액트코드는 원시코드로써, 복잡하지만 본질을 알아갈 수 있다.

```html
<div id="root"></div>
<script src="https://unpkg.com/react@17/umd/react.production.min.js"></script>
<script src="https://unpkg.com/react-dom@17/umd/react-dom.production.min.js"></script>
<script>
  const root = document.getElementById('root');
  const makespan = React.createElement(
    'span',
    { id: 'sexy', style: { color: 'red' } },
    'Hello World',
  );
  ReactDOM.render(makespan, root);
</script>
```

**react**는 엔진이며
**reactDOM**은 엔진을 html로 컨버팅해주는 라이브러리이다.
_?? 더 길다._  
요점은 이것이다. 기존 작업방식이 html->js였다면 리액트는js->html이다. 그리고 메인언어가 마크업언어에서 프로그래밍언어가 되면서 더 자유도가 높아진 것이다!!

```html
<div id="root"></div>
<script src="https://unpkg.com/react@17/umd/react.production.min.js"></script>
<script src="https://unpkg.com/react-dom@17/umd/react-dom.production.min.js"></script>
<script>
  let count = 0;
  const root = document.getElementById('root');
  const span = React.createElement('span', null, `Hello World! : ${count}`);
  const btn = React.createElement(
    'button',
    { onClick: () => console.log('hello world!!') },
    'Click!',
  );
  const container = React.createElement('div', null, [span, btn]);
  ReactDOM.render(container, root);
</script>
```

## jsx

이제 createElement를 쓰지 않겠다. 지금까지는 원시코드이지만 지금 설명하는 것은 ㄹㅇ 개발자들이 쓰는것이다. 애초에 원시코드를 다룰 기회는 거의 없다. jsx는 react코드를 **html문법**처럼 쓸수 있게 해준다.

```js
<script src="https://unpkg.com/react@17/umd/react.production.min.js"></script>
<script src="https://unpkg.com/react-dom@17/umd/react-dom.production.min.js"></script>
<script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
<script type="text/babel">
  const root = document.getElementById("root");
  const Title = () => <h3 id="title">Hello!</h3>;
  const Btn = () => (
    <button
      style={{ backgroundColor: "tomato" }}
      onClick={() => console.log("Hello World")}
    >
      Click!!
    </button>
  );
  const Container = () => (
    <div>
      <Title />
      <Btn />
    </div>
  );
  ReactDOM.render(<Container />, root);
</script>
```

태그들을 컴포넌트화 하고, 컨테이너에서 불러오고, 또 그 컨테이너를 루트div에 집어넣는 순서이다.
컴포넌트한 html 태그들은 첫글자를 대문자로 저장해야만 </>형태로 핸들링할 수 있다

[콘솔로그 두번찍힐때.](https://velog.io/@sweet_pumpkin/%EB%AC%B4%EC%9E%91%EC%A0%95-%EB%94%B0%EB%9D%BC%ED%95%98%EA%B8%B0-%EC%95%84%EB%8B%88-%EC%99%9C-%EC%BD%94%EB%93%9C%EA%B0%80-%EB%91%90-%EB%B2%88-%EC%B6%9C%EB%A0%A5%EB%90%98%EB%8A%94-%EA%B1%B4%EB%8D%B0-React-StrictMode)

```toc


```
