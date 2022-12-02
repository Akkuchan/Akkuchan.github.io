---
layout: single
title: "컴포넌트와 props의 개념 이해 "
categories: React
toc: true
author_profile: false
sidebar:
    nav: "docs"
---

# 컴포넌트
- 리액트는 컴포넌트들이 모여 페이지를 구성하다고 해도 과언이 아니다.
- 컴포넌트는 브라우저에서 하나의 부분, 조각의 개념이다.
- 같은 조각을 여러개 배치할 수도 있고 조금씩 변화를(색이나 크기 등등) 줄 수도 있다. 
- 한 화면에 같은 모양의 객체를 여러개 놓는다고 할 때, html코드로 복붙하듯이 놓는다면 코드의 중복이 발생하고 유지보수의 어려움이 있다.
- 리액트에서는 이를 해결하기 위해 컴포넌트라는 개념을 도입했다.
- 자바의 클래스처럼 하나의 상위 클래스, 즉 컴포넌트를 선언하고 이를 객체화(element)해 코드의 중복을 줄여 유지보수와 코드의 간결성을 높인 것이다. 

## 컴포넌트의 종류(함수 vs 클래스)
```javascript
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}
```
- 위의 코드는 props라는 객체의 인자값을 받아 element를 반환하는 함수형 컴포넌트를 나타낸다. 
- 말 그대로 인풋(props)을 받아 아웃풋(element)를 반환하는 메서드로서의 역할을 하는 컴포넌트이다.

- 이러한 코드를 ES6 Class라는 형태로도 만들 수 있다.

```javascript
class Welcome extends React.Component {
  render() {
    return <h1>Hello, {this.props.name}</h1>;
  }
}
```

## 컴포넌트의 특징
1. 모든 컴포넌트는 대문자로 시작해야한다.
- 소문자로 시작하면 DOM태그로 인식될 수 있다. 

## Props(property)
- 컴포넌트의 속성을 의미하는 개념
- 위에서 컴포넌트가 자바의 클래스같은 의미하고 했는데 이 props를 변경함으로서 같은 컴포넌트의 객체, 즉 element더라도 각기 다른 색상, 글자, 거리 같은 속성을 다르게 설정할 수 있게 된다. 
- 정리하면 컴포넌트에 전달할 다양한 정보를 담고 있는 자바스크립트 객체인 것.


### Props의 특징
- read-only
- 한번 설정되면 다시 이를 변경할 수가 없다.
- 이 또한 다른 props로 설정하려면 새로 element를 만들어야 한다. 
- 모든 리액트 컴포넌트는 props를 직접 바꿀 수 없고 같은 props에 대해서는 항상 같은 결과를 보여주어야 한다. (pure해야 한다.)

### props의 사용법
```javascript
function App(props){
    return (
    <Layout
        width={256}
        height={141}
        header={
            <Header title ="wewe블로그입니다." />
        }
        footer={
                <Footer />
            }
        />
    );
}
```


## 컴포넌트의 합성
- 컴포넌트들을 합쳐 하나의 컴포넌트를 만드는 것을 의미.
- 컴포넌트 내부에 컴포넌트를 가질 수 있기에 복잡한 화면을 컴포넌트로 나누어 구현할 수 있다. 

```javascript
function Welcom(props){
    return <h1>Hello, {props.name}</h1>
}

function App(props){
    return (
      <div>
        <Welcom name = "A" />
        <Welcom name = "B" />
        <Welcom name = "C" />
      </div>
    );
}
ReactDOM.render(<App />, document.getElementByUd('root'));
```
- App이라는 컴포넌트 안에 Welcom 이라는 자식 컴포넌트가 3개가 들어가 있다. 이렇게 컴포넌트들을 나누어 중첩함으로서 복잡한 컴포넌트 합성으로 보다 간결하고 읽기 쉽게 작성할 수 있다. 

## 컴포넌트의 추출
- 합성과 반대로 큰 컴포넌트를 잘게 나누어 새로운 컴포넌트를 만들어 내는 것. 
- 이를 통해 컴포넌트간의 특성과 기능이 뚜렷해져 재사용성과 개발속도가 증가한다. 
 