---
title: NPM 설치 과정에서 최신 버전의 Transitive Dependency가 선택되지 않는 문제
date: 2023-07-20 20:00:00 +0900
categories:
  - JavaScript
tags:
  - NPM설치
  - Transitive
  - Dependency
---

## 문제 상황 설명

Stack Overflow에 올라온 글에 따르면, 사용자는 NPM을 통해 패키지를 설치할 때 transitive dependency(간접 의존성)가 최신 버전으로 자동 업데이트되지 않는 문제를 겪고 있다. 이 경우에서 transitive dependency란, 사용자가 직접 설치한 패키지가 아니라 그 패키지가 의존하는 다른 패키지를 의미한다.

## 원인: 버전 잠금과 패키지 트리

NPM은 `package-lock.json` 또는 `yarn.lock` 파일을 통해 의존성 트리를 관리한다. 이 파일들은 특정 버전의 패키지가 어떤 버전의 다른 패키지에 의존하는지 정확한 정보를 가지고 있다. 이러한 잠금 파일이 있기 때문에, NPM은 이미 설치된 버전을 우선적으로 고려하게 된다.

## 해결 방법: 명령어와 설정 조절

1. **`npm update` 사용**: 이 명령어를 사용하면 NPM은 패키지의 최신 버전을 찾아 업데이트한다. 하지만 이 경우에도 `package-lock.json` 파일이 업데이트되므로 주의가 필요하다.

2. **`npm dedupe` 실행**: 중복된 패키지를 제거하여 의존성 트리를 최적화한다. 이 명령어 실행 후에도 `npm update`를 실행할 수 있다.

3. **`package-lock.json` 삭제**: 잠금 파일을 삭제하고 `npm install`을 다시 실행하면, 최신 버전의 의존성 패키지가 설치된다.

4. **`npm install <패키지>@latest`**: 특정 패키지를 최신 버전으로 명시적으로 업데이트한다.

## 주의 사항

- `npm update`나 `npm dedupe` 명령어 사용 시, 다른 패키지와의 호환성 문제가 발생할 수 있다.
- 잠금 파일을 삭제하는 것은 의존성 트리에 큰 변화를 가져올 수 있으므로 주의가 필요하다.

## 결론

NPM 설치 과정에서 최신 버전의 transitive dependency가 선택되지 않는 문제는 여러 가지 원인과 해결 방법이 있다. 명령어와 설정을 조절하여 이 문제를 해결할 수 있다.