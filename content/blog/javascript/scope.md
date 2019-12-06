<!-- ---
title: ' 스코프(Scope) '
date: 2019-11-18 21:59:60
category: 'JavaScript'
---

![](./images/scope/logo.png)

<center>'변수가 영향을 미치는 범위' 혹은 <strong style="color:#F6CF2F; font-size: 20px;">변수의 유효 범위</strong></center>

## **💎 목차**

- [정의 (Problem)](#-정의를-보며)
- [예제 (Solution)](#-예제을-보며)
- [복습 (Practice)](#-복습을-하며)

## **📕 정의를 보며**

스코프란, 한마디로 정의하면 '변수가 영향을 미치는 범위' 혹은

`변수의 유효 범위` 라고 할 수 있습니다.

스코프는 `전역 스코프`와 `지역 스코프` 두 가지 종류가 있습니다.

- 전역 스코프

변수가 함수 바깥이나 중괄호 바깥에 선언되었다면, 전역 스코프에 정의 되었다고 합니다.

- 지역 스코프

코드의 특정 부분에서만 사용할 수 있는 변수를 지역 스코프에 있다고 하며 이런 변수를 전역 변수라고 부릅니다.

<br />

**[⬆ 목차](#-목차)**

<hr />

## **📘 예제을 보며**

### 전역 스코프

전역 스코프는 변수가 함수 바깥이나 `{}` 바깥에서 선언되었다면, 전역 스코프에 정의 됩니다.

```js
const globalVariable = 'variable'
```

위와 같이 전역 변수를 선언한다면 코드 모든곳에서 `globalVariable` 변수를 사용할 수 있습니다.

```js
const globalVariable = 'variable'
function example() {
  console.log(globalVariable)
}

console.log(globalVariable) // 'variable'
example() // 'variable'
```

위와같이 전역 스코프를 이용하여 변수를 선언할 수 있지만 좋은 방법은 아닙니다.

왜냐하면, 두개 이상의 변수의 이름이 충돌하는 경우가 발생할수 있기 때문입니다.

```js
// 잘못된 예시
let variable = 'example'
let variable = 'example2'

// SyntaxError: Identifier 'variable' has already been declared
// 이미 같은 이름의 변수가 존재합니다.
```

만약 `var`를 이용하여 변수를 선언했다면, 두 번재 변수가 첫 번째 변수를 덮어쓰게됩니다.

```js
// var는 되도록 사용하지 않도록 합니다.
var variable = 'example'
var variable = 'example2'

// variable = 'example' -> 'example2'
```

위와같이 변수를 선언한다면 나중에 코드양이 많아졌을 때 디버깅을 하기 어려움을 겪기 때문에 되도록 `var`는 사용하지 않습니다.

<br />
<hr />

### 지역 스코프

지역 스코프는 코드에서 특정 부분에서만 사용이 가능한 변수입니다.

자바스크립트에서는 크게 두 가지의 지역 스코프가 존재합니다.

`함수 스코프`와 `블록 스코프`가 존재합니다.

#### 함수 스코프

함수 내부에서 변수를 선언하다면, 그 변수는 선언한 함수 내부에서만 사용이 가능합니다.

```js
function example() {
  const variable = 'example'
  console.log(variable)
}

example() // 'example'
console.log(variable) // Error, variable is not defined
```

#### 블록 스코프

블록 스코프는 여러분이 중괄호 `{}` 내부에서 `const`, `let`으로 변수 선언하면,

그 변수들은 중괄호 블록 내부에서만 사용이 가능합니다.

블록 스코프에는 `if {}`, `for {}`, `function {}` 등이 존재합니다.

```js
{
  const variable = 'example'
  console.log(variable) // 'example
}

console.log(variable) // Error, variable is not defined
```

<br />

**[⬆ 목차](#-목차)**

<hr />

## **📗 복습을 하며**

```js
var a = 10
function scope1() {
  a = 20
  console.log(a) // a = 20
}
scope1()
console.log(a) // a = 20

var b = 10
function scope2() {
  var b = 20
  console.log(b) // b = 20
}
scope2()
console.log(b) // b = 10
```

두 함수는 유사해보이지만 `console.log` 결과 값이 다르게 출력되는 것을 볼 수 있습니다.

scope1() `a = 20`, scope2() `var b = 20` 차이가 이러한 현상을 만들어 냅니다.

<br />

**[⬆ 목차](#-목차)**

<hr />

<br />

# 여러분의 댓글이 큰힘이 됩니다. (๑•̀ㅂ•́)و✧ -->
