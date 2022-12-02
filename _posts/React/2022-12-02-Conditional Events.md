---
layout: single
title: "조건부 렌더링 이해하기 "
categories: React
toc: true
author_profile: false
sidebar:
    nav: "docs"
---

# Conditional Rendering(조건부 렌더링)
- 조건부 렌더링은 렌더링을 하기에 앞서 특정 조건에 맞추어 렌더링이 달리 하기 위한 개념이다.
- 조건문을 렌더링이 적용하는 것이다. 

## Truth & falsy
- 트루는 아니나 트루로 여겨지고 폴스가 아니지만 폴스로 여겨지는 것을 의미.
- 자바스크립트에서는 true로 여겨지거나 false로 여겨지는 값들이 존재한다. 

```javascript
/* truty*/
true
{} (empty object)
[] (empty array)
42 (number, not zero)
"0", "false" (string, not empty)

/* falsy*/
false
0, -0(zero, minus zero)
0n (BigInt zero)
'', "",`` (empty string)
null
undefined
NaN(not a number)
```

## Elemen Variables
- 컴포넌트를 변수처럼 다루어 렌더링 조건을 설정하고 싶을 때 사용하는 변수이다.
```javascript
function LoginButton(props){
  return (
    <button onClick={props.onClick}>
    로그인
    </button>
  );

function LogoutButton(props){
  return (
    <button onClick={props.onClick}>
    로그아웃
    </button>
  );
}
```
```javascript
function LoginControl(props){
  const [isLoggedIn, setIsLoggedIn] = useState(false);
  const handleLoginClick= () =>{
    setIsLoggedIn(true);
  }
  const handleLoginClick= () =>{
    setIsLoggedIn(false);
  }

  let button;
  if(isLoggedIn){
    button = <LogoutButton onClick={handleLogoutClick} />;
  } else {
    button = <LoginButton onClick={handleLoginClick}>
  }
  return (
    <div>
    <Greeting isLoggedIn={isLogggedIn}/>
    <button>
    </div>
  )
}
```
- return문을 보면 button이라는 컴포넌트 객체를 받고 있는데 이는 위의 조건문에서 isLoggedIn의 조건에 따라 button 변수의 값이 LogoutButton or LoginButton으로 정해게되는 구조이다. 
- button이라는 변수가 두 컴포넌트 element중 하나를 받을 수 있게 되어 코드가 더 간결해진다. 

