---
title: Vue와 CKEditor를 이용하여 contenteditable 텍스트에 텍스트 삽입하기
date: 2023-08-09 20:00:00 +0900
categories:
  - JavaScript
tags:
  - Vue
  - CKEditor
---

## 문제 정의

CKEditor와 Vue.js를 사용하면서 `contenteditable` 속성을 가진 텍스트 영역에 새로운 텍스트를 삽입하고자 하는 경우가 있습니다. 이러한 경우에 어떻게 문제를 해결할 수 있는지에 대해 상세하게 설명하겠습니다.

## 에러 현상
에러 이름: 없음 (문제 상황만 존재)

## 해결 방법 1: CKEditor API 사용하기

CKEditor는 자체적인 API를 제공합니다. 이 API를 이용하면 사용자가 쉽게 텍스트를 삽입할 수 있습니다. CKEditor의 `editor.model` 객체를 이용하여 데이터를 변경하면 됩니다.

1. CKEditor 인스턴스를 가져옵니다.
2. `editor.model.change()` 메서드를 사용해 변경을 적용합니다.

```javascript
let editor = yourCkeditorInstance;
editor.model.change(writer => {
  let position = writer.createPositionAt(editor.model.document.getRoot(), 'end');
  writer.insertText('새로운 텍스트', position);
});
```

## 해결 방법 2: DOM 조작을 통한 방법

Vue.js를 이용해 DOM을 직접 조작하는 것도 가능한 방법입니다. 이렇게 하려면 다음과 같은 절차를 따르면 됩니다.

1. DOM 엘리먼트를 선택합니다.
2. `insertAdjacentHTML` 또는 `innerHTML` 속성을 이용해 새로운 텍스트를 삽입합니다.

```javascript
let element = document.querySelector('[contenteditable]');
element.insertAdjacentHTML('beforeend', '새로운 텍스트');
```

이 방법은 CKEditor API를 사용하는 것보다 조금 더 복잡할 수 있으나, 직접 DOM을 조작하고 싶을 때 사용할 수 있습니다.

## 결론

Vue와 CKEditor를 사용하면서 텍스트를 삽입하는 방법은 주로 두 가지입니다. 첫 번째는 CKEditor의 자체 API를 사용하는 것이고, 두 번째는 DOM 조작을 통해 직접 텍스트를 삽입하는 것입니다. 필요에 따라 적절한 방법을 선택하여 구현할 수 있습니다.