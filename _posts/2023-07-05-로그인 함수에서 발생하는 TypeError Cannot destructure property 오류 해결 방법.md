---
title: 로그인 함수에서 발생하는 TypeError Cannot destructure property 오류 해결 방법
date: 2023-07-05 20:00:00 +0900
categories:
  - JavaScript
tags:
  - TypeError
---

## 오류 상황 설명

로그인 함수를 실행하다 보면 `TypeError: Cannot destructure property` 라는 오류 메시지가 나타날 수 있습니다. 이 오류는 JavaScript에서 객체나 배열에서 특정 값을 분해할 때(destructuring) 발생합니다. 이런 경우는 코드에 논리적인 오류나 문법 오류가 있는 것이므로 정확하게 어떤 부분에서 문제가 생겼는지 파악해야 합니다.

## 오류의 원인

이 오류는 대체로 두 가지 주된 원인에서 발생합니다.

1. **분해하려는 객체나 배열이 `null`이나 `undefined`일 경우**: 변수에 값이 할당되지 않아 발생하는 오류입니다.
2. **잘못된 변수명이나 키 값 사용**: 객체나 배열에서 분해하려는 값의 이름이 잘못된 경우 발생합니다.

## 해결 방법

### 객체나 배열이 `null`이나 `undefined`인 경우

이런 경우에는 조건문을 사용하여 해당 값이 존재하는지 먼저 확인합니다. 존재하지 않을 경우 기본 값을 설정해줄 수 있습니다.

```javascript
const { username, password } = user || {};
```

### 잘못된 변수명이나 키 값 사용

이 오류는 대체로 코드를 복사하고 붙여넣을 때나 오타로 인해 발생합니다. 변수나 키 값의 이름을 정확하게 확인해주세요.

```javascript
const { userName, passWord } = user; // 올바른 변수명을 사용하세요.
```

## 마무리

`TypeError: Cannot destructure property` 오류는 주로 객체나 배열을 분해할 때 발생합니다. 오류 메시지가 나타나면, 먼저 분해하려는 객체나 배열이 `null`이나 `undefined`인지, 또는 변수명이나 키 값이 올바른지 확인해보세요. 이렇게 문제를 파악하고 적절한 조치를 취하면 이 오류를 쉽게 해결할 수 있습니다.