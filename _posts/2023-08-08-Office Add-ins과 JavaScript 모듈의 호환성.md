---
title: Office Add-ins과 JavaScript 모듈의 호환성
date: 2023-08-08 20:00:00 +0900
categories:
  - JavaScript
tags:
  - 자바스크립트모듈
---

## 문제 정의: Error Name - DoesNotExist

사용자들이 Office Add-ins을 개발할 때 자주 마주치는 질문 중 하나는 이것이 JavaScript 모듈과 호환되는지 여부입니다. 이 문제의 핵심은 다양한 JavaScript 모듈 구조를 사용하여 개발을 하고 싶은데, Office Add-ins에서 이를 지원하지 않을 경우에는 개발 프로세스에 어려움이 생길 수 있다는 점입니다.

## 기술적 배경

JavaScript 모듈은 코드를 모듈화하여 관리할 수 있게 해주는 구조입니다. ES6(ECMAScript 2015)에서부터 공식적으로 지원하기 시작했고, `import`와 `export` 구문을 통해 모듈을 불러오거나 내보낼 수 있습니다. 예를 들어, `import React from 'react';`은 React 라이브러리를 불러오는 코드입니다.

Office Add-ins은 Microsoft Office 프로그램에 기능을 추가하는 작은 프로그램입니다. 이것은 대개 JavaScript API를 사용해서 개발됩니다.

## 호환성 여부

Office Add-ins은 기본적으로 JavaScript를 지원하기 때문에 JavaScript 모듈과의 호환성이 기본적으로 있습니다. 그러나 몇 가지 주의할 점이 있습니다.

1. **버전 문제**: Office JavaScript API의 버전과 모듈이 지원하는 ECMAScript 버전이 같아야 합니다.
2. **API 제한**: 특정 Office API가 모듈과 호환되지 않을 수 있으므로, API 문서를 꼼꼼히 확인해야 합니다.
3. **로딩 시간**: 모듈이 많아질수록 애드인의 로딩 시간이 길어질 수 있으므로, 필요한 모듈만 import 하는 것이 좋습니다.

## 결론

Office Add-ins과 JavaScript 모듈은 기본적으로 호환됩니다. 그러나 버전 문제, API 제한, 로딩 시간 등을 고려해야 하며, 이러한 부분을 신경 써서 개발을 해야 합니다. 따라서 Office Add-ins을 개발할 때는 이러한 요소들을 충분히 고려해야 할 필요가 있습니다.