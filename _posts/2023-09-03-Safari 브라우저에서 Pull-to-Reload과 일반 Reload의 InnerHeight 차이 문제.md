---
title: Safari 브라우저에서 Pull-to-Reload과 일반 Reload의 InnerHeight 차이 문제
date: 2023-09-03 20:00:00 +0900
categories:
  - JavaScript
tags:
  - Safari
  - InnerHeight
---

## 문제 상황

Stackoverflow에 올라온 질문에 따르면, Safari 브라우저에서 웹페이지를 새로고침할 때 `pull-to-reload` 기능과 일반 `reload` 기능을 사용하면 다른 `innerHeight` 값을 반환한다고 합니다. 이 차이가 발생하는 이유와 해결 방법에 대해 자세히 알아봅시다.

## innerHeight란 무엇인가?

`innerHeight`는 웹페이지에서 화면의 내부 높이를 픽셀 단위로 반환하는 자바스크립트 속성입니다. 보통 이 값을 사용해 레이아웃을 조절하거나 다양한 UI 이벤트를 처리합니다.

## 원인: Pull-to-Reload과 일반 Reload의 차이

`Pull-to-Reload`은 사용자가 손가락을 화면에 대고 아래로 당겨서 페이지를 새로고침하는 기능입니다. 일반 `Reload`는 브라우저의 새로고침 버튼을 누르거나 `F5`키를 누르는 등의 방식으로 페이지를 새로고침합니다.

이 두 가지 방법은 내부적으로 페이지를 새로 로드하는 메커니즘이 다르기 때문에 `innerHeight` 값이 다를 수 있습니다. 예를 들어, `Pull-to-Reload`는 일반적으로 빠른 새로고침을 목표로 하기 때문에 일부 레이아웃 계산이 덜 정밀할 수 있습니다.

## 해결 방법: 자바스크립트로 강제 조정

이 문제를 해결하기 위한 방법 중 하나는 `window.addEventListener`를 사용해 페이지가 완전히 로드된 후에 `innerHeight` 값을 강제로 조정하는 것입니다.

```javascript
window.addEventListener("load", function() {
    // 원하는 innerHeight 값으로 조정
    document.documentElement.style.height = window.innerHeight + "px";
});
```

이렇게 하면 `pull-to-reload`와 일반 `reload`에서 반환되는 `innerHeight` 값을 동일하게 만들 수 있습니다.

## 정리

Safari 브라우저에서 `pull-to-reload`과 일반 `reload`을 사용할 때 `innerHeight` 값이 다르게 나타나는 문제는 내부적인 로딩 메커니즘의 차이 때문입니다. 이를 해결하기 위해서는 페이지 로드 후에 `innerHeight` 값을 자바스크립트로 강제로 조정하는 방법을 사용할 수 있습니다. 이 방법은 웹페이지의 레이아웃을 안정적으로 유지할 수 있게 도와줍니다.