---
layout: single
title: "Lifting State Up"
categories: React
toc: true
author_profile: false
sidebar:
    nav: "docs"
---

# Lifting State
- 여러 컴포넌트에서 공동의 state를 공유하는 방법

## Shared State
- 여러 컴포넌트에서 공동의 state를 공유하여 자원을 효율적으로 사용할 수 있다.
- 이는 부모-자식 컴포넌트간의 상속 관계에서 자식 컴포넌트가 부모 컴포넌트의 state를 가져와 사용하는 구조로 많이 구현된다. 
- 그리고 이 공유된 state를 셰어드 스테이트라고 한다.
- 여러 자식 컴포넌트는 부모 컴포넌트로부터 state를 가져와 원하는 대로 알아서 활용할 수 있다. 
- 

## 예제코드
```javascript
const scaleNames = {
    c: "섭씨",
    f: "화씨",
};

function TemperatureInput(props){
    const handleChange = (event) => {
        props.onTemperatureChange(event.target.value );
    };

    return(
        <fieldset>
            <legend>
                온도를 입력해주세요(단위:{scaleNames[props.scale]});
            </legend>
            <input value={props.temperature} onChange={handleChange} />
        </fieldset>
    );
}

expert default TemperatureInput
```
```javascript
import React, {useState} from "react";
import TemperatureInput from "./TemperatureInput";

function BoilingVerdict(props){
    if(props.celsius>=100){
        return <p>물이 끓습니다</p>;
    }
    return <p>물이 끓기 않습니다.</p>;
}

function toCelsius(fahrenheit){
    return (fahrenheit-32) * 5 / 9;
}

function toFahrenheit(celcius){
    return (celsius*9)/5+32;
}

function tryConvert(temperature, convert){
    const input = parseFloat(temperature);
    if(Number.isNaN(input)){
        return "";
    }
    const output = convert(input);
    const rounded = Math.round(output*1000)/1000;
    return rounded.toString();
}

function Calculator(props){
    const [temperature, setTemperature] = useState("");
    const [scale, setScale] = useState("c");
    
    const handleCelsiusChange = (temperature) => {
        setTemperature(temperature);
        setScale("c");
    };

    const handleFahrenheitChange = (temperature) => {
        setTemperature(temperature);
        setScale("f");
    };

    const celsius = 
        scale === "f" ? tryConvert(temperature, toCelsius) : temperature;
    const fahrenheit = 
        scale ==="c" ? tryConvert(temperature, toFahrenheit) : temperature;

    return(
        <div> 
            <TemperatureInput
                scale="c"
                temperature={celsius}
                onTemperatureChange={handleCelsiusChange}
                />
            <TemperatureInput
                scale="f"
                temperature={fahrenheit}
                onTemperatureChange={handleFahrenheitChage}
            />
            <Boilingverdict celsius={parseFloat(celsius)} />
        </div>
    );
}

export default Calculator;

```