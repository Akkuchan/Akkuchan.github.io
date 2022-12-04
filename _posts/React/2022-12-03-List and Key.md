---
layout: single
title: "List & Key 활용"
categories: React
toc: true
author_profile: false
sidebar:
    nav: "docs"
---

# List
- 자바스크립트에서는 배열을 통해 List를 구현한다.
```javascript
const array = [1,2,3,4,5]; 
```

# map()
- javascript에서 map은 다음과 같이 사용된다.
```javascript
const doubled = numbers.map((number) => number*2);
```
- 배열의 요소(number)를 하나씩 가져와 특정 작업을 수행(*2)하고 이를 배열로 반환(doubled)한다. 


```javascript
const numbers = [1,2,3,4,5];
const listItems = numbers.map((number) => <li>{number}</li>);

ReactDOM.render(
  <ul>{listItems}</ul>,
  document.getElementById('root');
)
```
- 이처럼 활용 가능하다. 

## map 사용시 주의사항
- key는 고유한 식별 문자열을 의미한다. 
- 때문에 key값으로 id값이나 index를 사용하기도 한다.
- 다만 인데스의 경우 배열의 값의 인덱스가 변경되어 순서가 바뀐다는 점은 주의해야 한다.
- 리액트는 따로 설정하지 않으면 인덱스를 키값으로 설정한다. 
- map에서 내부 값이 element라면 무조건 요소마다 각각의 key값을 설정해주어야 한다. 