---
title: 드롭다운 버튼 만들기 HTML, CSS, JS
date: 2023-07-21 20:00:00 +0900
categories:
  - JavaScript
tags:
  - 드롭다운
---

## 드롭다운 버튼이란?

드롭다운 버튼이란, 클릭하면 여러 선택지가 나타나는 버튼을 말합니다. 웹사이트에서 주로 메뉴나 다른 옵션을 선택할 때 사용됩니다.

## HTML 구조 작성하기

HTML에서 드롭다운 버튼을 만들기 위해서는 `<button>` 요소와 `<div>` 요소가 필요합니다. 이를 통해 버튼과 클릭 시 나타날 목록을 생성할 수 있습니다.

```html
<button id="dropdownButton">클릭하세요</button>
<div id="dropdownMenu" style="display:none;">
  <a>옵션 1</a>
  <a>옵션 2</a>
  <a>옵션 3</a>
</div>
```

## CSS 스타일링

CSS를 사용하여 드롭다운 메뉴에 적절한 스타일을 적용할 수 있습니다. 예를 들어, `display: none;` 속성을 이용하여 기본적으로 메뉴가 안 보이게 설정할 수 있습니다.

```css
#dropdownMenu {
  display: none;
  position: absolute;
}
```

## JavaScript로 동작 추가하기

JavaScript를 사용하여 버튼을 클릭했을 때 드롭다운 메뉴가 나타나거나 사라지게 할 수 있습니다.

```javascript
document.getElementById("dropdownButton").addEventListener("click", function() {
  const menu = document.getElementById("dropdownMenu");
  if(menu.style.display === "none") {
    menu.style.display = "block";
  } else {
    menu.style.display = "none";
  }
});
```

이 코드는 'click' 이벤트를 감지하여 메뉴의 `display` 속성을 변경합니다.

## 자주 발생하는 오류: Uncaught TypeError

만약 위 코드를 실행할 때 "Uncaught TypeError: Cannot read property 'addEventListener' of null"이라는 오류가 발생한다면, 스크립트가 HTML보다 먼저 로드되어 버튼 요소를 찾을 수 없기 때문입니다. 이를 해결하기 위해서는 스크립트를 HTML의 마지막 부분에 위치시키거나, `DOMContentLoaded` 이벤트를 사용하세요.

---

이렇게 HTML, CSS, JavaScript를 활용하여 드롭다운 버튼을 구현할 수 있습니다. 각 단계별로 필요한 코드와 속성을 알아보았으니, 이를 활용하여 다양한 웹 페이지에서 유용하게 사용해보세요.