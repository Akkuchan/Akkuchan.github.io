---
layout: single
title: "prevState 개념 이해 "
categories: React
toc: true
author_profile: false
sidebar:
    nav: "docs"
---

# prevState
- 리액트에서는 state의 값을 변경할 때, 바로 state를 초기화하는 것이 아니라 setState()를 통해 변겨해야 한다.
- 여기서 prevState라는 것은 setState()에 전달한 매개변수를 뜻하는 단어이다. 
- 이 prevState는 setState가 렌더링되어 컴포넌트의 state가 변경되기 전에 해당 값을 가져와 사용하기 위해서 쓰이은 변수이다.  

``` javascript
state = {
   count: 0
}
updateCount = () => {
    this.setState({ count: this.state.count + 1});
    this.setState({ count: this.state.count + 1});
    this.setState({ count: this.state.count + 1});
    this.setState({ count: this.state.count + 1});
}

```
- 이 코드에서 setState로 count라는 state를 변경하는 코드를 여러번 사용하였지만 실제 코드는 단 한번, 마지막 코드만 수행한다.
- 왜냐하면 setState는 함수가 종료된 후에 state의 값을 변경하기 때문이다. 
- 따라서 updateCount라는 함수 내부에서 state를 따로 처리하여면 렌더링되기 이전의(prev) state값을 콜백해야 한다.

```javascript
updateCount = () => {
    this.setState(prevstate => ({ count: prevstate.count + 1}));
    this.setState(prevstate => ({ count: prevstate.count + 1}));
    this.setState(prevstate => ({ count: prevstate.count + 1}));
    this.setState(prevstate => ({ count: prevstate.count + 1}));
}
```
- 이전 코드와 달리 prevstate라는 state를 계속 불러와 +1을 해주고 있다. 첫 setState에서 prevState라는 값은 해당 컴포넌트(this)의 state를 의미한다. 이를 가져와(=>) count state를 +1 한다.ㅈ
- 이는 컴포넌트의 state인 count를 바꾼 것이 아닌 그 이전 상태인 prevState의 state값 중 하나인 count를 변경한 것이다. 
- 이것이 4번 반복되고 이후 함수가 종료되면 그때서야 setState함수가 컴포넌트의 state를 변경하는 것.
- 이렇게 함수 내에서 state를 다루기 위해서 사용하는 변수가 바로 prevState인 것이다. 

참고
https://stackoverflow.com/questions/54807454/what-is-prevstate-in-reactjs