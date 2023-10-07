---
title: JavaScript로 엑셀 파일 생성 시 행이나 셀에 색상 추가하기
date: 2023-07-11 20:00:00 +0900
categories:
  - JavaScript
tags:
  - 자바스크립트
  - 엑셀
  - Excel
---

## 개요

이 글에서는 JavaScript를 이용하여 엑셀 파일을 생성할 때 특정 행이나 셀에 색상을 추가하는 방법에 대해 상세히 알아봅니다. 이 작업은 데이터 시각화를 향상시키고, 사용자가 특정 정보를 빠르게 파악할 수 있게 도와줍니다.

## 필요한 도구

- JavaScript
- 라이브러리 (예: `xlsx`)

## 코드 기초

먼저, `xlsx` 라이브러리를 사용하여 기본적인 엑셀 파일을 생성해야 합니다. 이 라이브러리는 엑셀 파일을 조작할 수 있는 다양한 도구를 제공합니다.

```javascript
const XLSX = require('xlsx');
const wb = XLSX.utils.book_new();
const ws = XLSX.utils.aoa_to_sheet([
  ["이름", "나이"],
  ["철수", 25],
  ["영희", 23]
]);
XLSX.utils.book_append_sheet(wb, ws, "시트1");
XLSX.writeFile(wb, 'sample.xlsx');
```

## 셀 색상 변경하기

셀에 색상을 추가하려면 `s` 속성을 사용해야 합니다. 이 속성에는 배경색(`bgColor`), 글자색(`fgColor`) 등을 설정할 수 있습니다.

```javascript
ws['A1'].s = {
  fill: {
    bgColor: { rgb: "FFFF00" },
    fgColor: { rgb: "FFFF00" }
  }
};
```

## 행 색상 변경하기

행에 색상을 변경하려면 해당 행의 모든 셀에 대한 스타일을 변경해야 합니다. 다음 코드는 첫 번째 행의 모든 셀에 노란색을 적용하는 예입니다.

```javascript
for (let i = 0; i < 2; i++) {
  let cell = XLSX.utils.encode_cell({ r: 0, c: i });
  ws[cell].s = {
    fill: {
      bgColor: { rgb: "FFFF00" },
      fgColor: { rgb: "FFFF00" }
    }
  };
}
```

## 결론

JavaScript와 `xlsx` 라이브러리를 사용하면 엑셀 파일에 쉽게 색상을 추가할 수 있습니다. 이 기능은 데이터를 더 쉽게 이해하고 분석하는 데 도움이 됩니다. 이제 이 코드를 사용하여 색상을 자유롭게 조작해보세요.