---
title: Google Apps Script에서 showModalDialog 함수와 트리거 사용하기
date: 2023-07-15 20:00:00 +0900
categories:
  - JavaScript
tags:
  - 구글
  - Google
  - showModalDialog
---

## 문제 상황: `showModalDialog`와 트리거를 함께 쓰는 방법

Google Apps Script에서 트리거와 `showModalDialog` 함수를 함께 사용하려고 할 때 어려움을 겪고 있다면, 여기에 해결책이 있습니다. 트리거는 자동으로 코드를 실행하는 조건이나 이벤트를 의미하고, `showModalDialog`는 사용자에게 팝업 창을 보여주는 함수입니다. 이 두 가지를 함께 사용하면 여러가지 문제가 생길 수 있습니다. 대표적인 문제는 `Authorization Mode` 문제입니다.

## 에러: `Authorization Mode`

`Authorization Mode`라는 용어는 권한 모드를 의미합니다. 특히 Google Apps Script에서는 사용자의 권한을 필요로 하는 여러 기능이 있습니다. `showModalDialog` 함수는 사용자 인터페이스에 영향을 주기 때문에 실행을 위해서는 사용자의 권한이 필요합니다. 트리거를 사용할 경우 이 권한 문제가 발생할 수 있으며, 이로 인해 코드 실행에 실패할 수 있습니다.

## 해결 방법 1: HTML Service와 Google Script 통합

HTML Service를 사용하여 별도의 HTML 파일을 만듭니다. 그리고 이 HTML 파일에서 자바스크립트를 통해 Google Apps Script 함수를 호출할 수 있습니다. 이 방식을 통해 사용자 인터페이스를 생성하고, 트리거를 설정하여 자동화 작업을 할 수 있습니다.

```javascript
// Google Apps Script 코드 예시
function showDialog() {
  var html = HtmlService.createHtmlOutputFromFile('Page')
      .setSandboxMode(HtmlService.SandboxMode.IFRAME)
      .setWidth(400)
      .setHeight(300);
  SpreadsheetApp.getUi().showModalDialog(html, 'My Dialog');
}
```

## 해결 방법 2: 사용자 액션을 트리거로 설정

트리거로 설정 가능한 사용자 액션을 활용하여 `showModalDialog`를 호출하는 것도 하나의 방법입니다. 예를 들어, 사용자가 특정 셀을 클릭하거나, 특정 데이터를 입력했을 때 `showModalDialog`를 실행시키는 것입니다.

## 정리

Google Apps Script에서 `showModalDialog`와 트리거를 함께 사용하려면 권한 문제를 해결해야 합니다. 이를 위한 두 가지 방법으로는 HTML Service를 통한 통합과 사용자 액션을 트리거로 설정하는 것이 있습니다. 이 두 가지 방법을 통해 문제를 해결하고 원하는 기능을 구현할 수 있습니다.