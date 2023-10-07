---
title: Handlebars.js에서 논리 연산자 사용하기
date: 2023-07-29 20:00:00 +0900
categories:
  - JavaScript
tags:
  - HandlebarsJS
---

## 문제 상황: `if` 조건문에서 논리 연산자를 사용하고 싶다

Handlebars.js를 사용하면서 `if` 조건문에서 논리 연산자(AND, OR 등)를 사용하려고 했지만, 기본적으로는 지원되지 않는 것을 발견했습니다. 여기에는 그 해결 방법들을 제공하려고 합니다.

## 해결방법 1: 헬퍼 함수 사용하기

헬퍼(helper) 함수는 Handlebars에 추가적인 기능을 제공하는 역할을 합니다. 예를 들어, 논리 연산을 하려면 다음과 같이 헬퍼 함수를 만들 수 있습니다.

```javascript
Handlebars.registerHelper('ifCond', function(v1, operator, v2, options) {
  switch (operator) {
    case '==':
      return (v1 == v2) ? options.fn(this) : options.inverse(this);
    case '===':
      return (v1 === v2) ? options.fn(this) : options.inverse(this);
    // 여기에 다른 연산자들을 추가할 수 있습니다.
    default:
      return options.inverse(this);
  }
});
```

## 해결방법 2: `#if`와 `#unless` 조합하기

`#if`와 `#unless` 헬퍼를 조합하여 일종의 논리 연산을 흉내낼 수 있습니다. 예를 들어 "AND" 연산을 하려면 다음과 같이 사용할 수 있습니다.

```handlebars
{{#if condition1}}
  {{#if condition2}}
    <!-- condition1 AND condition2 가 true일 때 실행됩니다 -->
  {{/if}}
{{/if}}
```

## 해결방법 3: 서버에서 논리 연산 처리

서버에서 미리 논리 연산을 수행하여, 그 결과를 템플릿으로 전달할 수 있습니다. 이 방법은 로직을 템플릿에서 분리하므로 코드 관리가 더 쉽습니다.

## 요약

Handlebars.js에서는 기본적으로 논리 연산자를 지원하지 않습니다. 하지만 헬퍼 함수를 사용하거나 `#if`와 `#unless`를 조합하는 방법, 또는 서버에서 논리 연산을 미리 처리하는 방법으로 이를 해결할 수 있습니다. 이러한 방법들을 통해 더 복잡한 조건문을 구현할 수 있습니다.