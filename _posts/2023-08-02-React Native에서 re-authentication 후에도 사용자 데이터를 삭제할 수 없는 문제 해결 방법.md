---
title: React Native에서 re-authentication 후에도 사용자 데이터를 삭제할 수 없는 문제 해결 방법
date: 2023-08-02 20:00:00 +0900
categories:
  - JavaScript
tags:
  - ReactNative
  - 사용자데이터삭제
---

## 문제 상황: 사용자 데이터 삭제 실패 (`auth/requires-recent-login`)

React Native와 Firebase를 사용할 때, 사용자 데이터를 삭제하기 위해 다시 인증(re-authentication)을 하더라도 `auth/requires-recent-login` 오류가 발생하는 문제가 있다. 이 문제는 사용자의 최근 로그인 시간이 오래되었을 때 Firebase에서 일어나는 보안 문제로 볼 수 있다.

## 해결 방법 1: 재인증 코드 삽입 위치 확인

코드 내에서 `signInWithEmailAndPassword` 함수를 사용하여 재인증을 수행한 후, 바로 `delete` 함수를 호출하는 것이 중요하다. 이 두 함수 사이에 다른 로직이 들어가면 Firebase가 최근 로그인으로 인식하지 않을 수 있다.

```javascript
async function reauthenticateAndDelete(email, password) {
  const user = firebase.auth().currentUser;
  const credential = firebase.auth.EmailAuthProvider.credential(email, password);

  // 재인증
  await user.reauthenticateWithCredential(credential);

  // 사용자 데이터 삭제
  await user.delete();
}
```

## 해결 방법 2: 비동기 함수 관리

JavaScript의 `async`와 `await`를 적절하게 사용하여 함수가 완전히 종료된 후에 다음 함수가 실행되도록 해야한다. 그렇지 않으면, `delete` 함수가 `reauthenticateWithCredential` 함수의 완료를 기다리지 않고 실행될 수 있으며, 이러한 상황에서도 `auth/requires-recent-login` 오류가 발생할 수 있다.

## 해결 방법 3: 에러 핸들링 추가

`try`와 `catch` 문을 사용하여 `delete` 함수에서 발생하는 에러를 캐치할 수 있다. 이를 통해 코드가 어느 부분에서 실패하는지 정확하게 파악할 수 있다.

```javascript
async function reauthenticateAndDelete(email, password) {
  try {
    const user = firebase.auth().currentUser;
    const credential = firebase.auth.EmailAuthProvider.credential(email, password);

    await user.reauthenticateWithCredential(credential);
    await user.delete();
  } catch (error) {
    console.error("Error:", error.code); // 에러 코드는 영어로 출력
  }
}
```

이러한 방법들을 통해 React Native에서 `auth/requires-recent-login` 오류를 해결할 수 있다. 문제 해결을 위한 각 단계를 철저하게 따르면 이 문제를 효과적으로 해결할 수 있다.