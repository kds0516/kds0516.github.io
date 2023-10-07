---
title: TestComplete에서 Intellisense와 JSDoc를 위한 jsconfig 설정
date: 2023-07-23 20:00:00 +0900
categories:
  - JavaScript
tags:
  - TestComplete
  - Intellisense
  - JSDoc
  - jsconfig
---

## 문제 상황

프로그래밍을 할 때, 자동 완성과 문서화 기능은 매우 중요하다. JavaScript를 사용하는 SmartBear의 TestComplete라는 테스트 자동화 도구에서도 이러한 기능들이 필요하다. 그러나 이를 설정하는 방법이 명확하지 않은 경우가 많다. 여기서는 `jsconfig.json`을 사용하여 Intellisense(자동 완성)와 JSDoc(문서화)를 어떻게 설정할 수 있는지에 대해 알아본다.

> Intellisense: 코드를 더 빠르고 정확하게 작성할 수 있도록 자동 완성, 변수 타입 추론, 함수 시그니처 정보 등을 제공하는 기능입니다.
>
> JSDoc: JavaScript 코드에 대한 문서를 작성하고 유지 관리하기 위한 주석 형식입니다.

## jsconfig.json이란?

`jsconfig.json` 파일은 JavaScript 프로젝트의 루트 디렉토리에 위치하는 설정 파일이다. 이 파일을 통해 TypeScript 컴파일러에게 프로젝트의 루트 파일이 무엇인지, 어떤 파일들을 포함하거나 제외할 것인지 등을 지정할 수 있다. 이 정보가 TestComplete에서도 사용되어, Intellisense와 JSDoc 기능을 최적화할 수 있다.

## TestComplete에서의 설정 방법

### 1단계: jsconfig.json 파일 생성

프로젝트 루트 디렉토리에 `jsconfig.json` 파일을 생성한다. 이 파일에는 다음과 같이 기본 설정을 넣는다.

```json
{
  "compilerOptions": {
    "target": "es6",
    "module": "commonjs"
  },
  "exclude": ["node_modules"]
}
```

### 2단계: JSDoc 주석 추가

코드 내에서 함수나 변수 위에 JSDoc 형식의 주석을 추가한다.

```javascript
/**
 * 두 숫자를 더한다.
 * @param {number} a - 첫 번째 숫자
 * @param {number} b - 두 번째 숫자
 * @returns {number} 두 숫자의 합
 */
function add(a, b) {
  return a + b;
}
```

### 3단계: TestComplete 재시작

설정을 적용하려면 TestComplete 프로그램을 재시작한다.

## 결과

이 설정을 마치고 나면, TestComplete 내에서 JavaScript 코드 작성 시 자동 완성과 문서화 기능을 더 효과적으로 사용할 수 있다. 이를 통해 코드의 품질을 높이고, 작성 속도를 향상시킬 수 있다.