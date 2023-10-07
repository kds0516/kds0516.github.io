---
title: Playwright 테스팅에서 Mock API 문제 해결하기
date: 2023-07-13 20:00:00 +0900
categories:
  - JavaScript
tags:
  - MockAPI
---

## 문제 상황: "Mock API Issue in Playwright Testing"

스택오버플로우에서 볼 수 있는 문제는 Playwright 테스팅 중 Mock API에서 어려움을 겪고 있다는 것입니다. 여기서 'Mock API'는 실제 서버와 통신하지 않고 테스트 환경에서 사용되는 가상의 API를 의미합니다. 'Playwright'는 브라우저 자동화 및 테스팅을 위한 라이브러리입니다.

## 해결 방안 1: 응답 확인

먼저 Mock API가 올바른 응답을 반환하는지 확인해야 합니다. '올바른 응답'은 테스트 조건에 맞는 데이터 형식과 상태 코드를 의미합니다. 이를 확인하려면 Playwright의 `intercept` 메서드를 사용하여 네트워크 요청을 가로챌 수 있습니다.

```javascript
await page.route('**/api/resource', (route) => {
  route.fulfill({
    status: 200,
    body: JSON.stringify({ key: 'value' }),
  });
});
```

## 해결 방안 2: 적시 동기화

테스트 중 Mock API 응답이 늦게 오면 문제가 발생할 수 있습니다. Playwright는 `waitForResponse` 메서드를 제공하여 이 문제를 해결할 수 있습니다.

```javascript
await page.waitForResponse('**/api/resource');
```

## 해결 방안 3: 캐시 문제

브라우저 캐시 때문에 원치 않는 데이터가 반환될 수 있습니다. 이를 해결하기 위해 테스트 시작 전에 캐시를 비워야 합니다.

```javascript
await page.evaluate(() => {
  localStorage.clear();
  sessionStorage.clear();
});
```

## 주의 사항: 이슈 이름은 "Mock API Issue in Playwright Testing"

테스트 중 문제가 계속된다면 문제의 원인이 될 수 있는 부분을 차례로 확인해야 합니다. 위의 해결 방안들은 일반적인 문제를 해결할 수 있는 방법이며, 구체적인 문제 상황에 따라 다르게 적용될 수 있습니다.