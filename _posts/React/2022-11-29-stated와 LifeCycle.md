---
layout: single
title: "State와 LifeCycle 이해하기 "
categories: React
toc: true
author_profile: false
sidebar:
    nav: "docs"
---

# State
- 리액트 컴포넌트의 변경가능한 데이터를 의미한다. 
- 이는 개발자가 각자 정의해서 사용한다.
- 주의할 것은 렌더링이나 데이터 흐름에 사용되는 값만 state에 포함해야 한다는 것.
  - staet 값은 변경될 경우 컴포넌트가 재렌더링되기에 과도할 경우 성능이 저하되기 때문이다. 
  - 관련 없는 값은 컴포넌트의 인스턴스값으로 남겨두면 된다고 한다.
- state의 형태는 props처럼 자바스크립트 객체형태이다. 

모든 클래스 컴포넌트는 생성자를 갖고있다.
    
## State의 특징
- state는 직접 수정할 수 없다. 더 정확히는 하면 안 된다.

```javascript
//잘못된 직접 수정
this.state={
  name:'Inje'
};
//올바른 함수를 통한 수정
this.setState={
  name:'Inje'
};
```

# LifeCycle
- 리액트 컴포넌트의 생명주기를 의미한다.
<img src= https://cdn.filestackcontent.com/ApNH7030SAG1wAycdj3H></img>
1.Mount:컴포넌트의 생성을 의미. 생성자를 통해 컴포넌트가 만들어짐
2.update: props가 변경되거나 state가 바뀌거나하는 변화 과정을 의미
3.unmount: 더이상 화면에 표시하지 않을 때, 컴포넌트를 해소하는 것을 의미.
- 컴포넌트는 시간 흐름에 따라 생성되고 업데이트되고 사라진다. 