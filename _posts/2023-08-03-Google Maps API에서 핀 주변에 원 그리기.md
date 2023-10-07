---
title: Google Maps API에서 핀 주변에 원 그리기
date: 2023-08-03 20:00:00 +0900
categories:
  - JavaScript
tags:
  - 구글맵API
---

## 문제 개요

Google Maps API를 사용하면 지도에 여러 기능을 적용할 수 있습니다. 그 중 하나는 지도에 핀(마커)을 추가하는 것인데, 이때 핀 주변에 원을 그려 추가적인 정보를 표시하고 싶을 수 있습니다. 여기서는 Stack Overflow에서 나온 `Using Google Maps importLibrary API, want to add a circle around pin`이라는 질문에 대한 해결 방법을 다룹니다.

## 코드 오류: None Specified

질문에서 특정 코드 오류는 지정되지 않았습니다.

## 원 그리기의 필요성

핀 주변에 원을 그리는 것은 여러 가지 이유로 유용할 수 있습니다. 예를 들어, 특정 지점에서 일정 거리 내에 있는 것을 시각적으로 표현하거나, 안전한 거리를 유지해야 하는 경우에 유용하게 사용할 수 있습니다. 

## 해결 방법

### 1. Google Maps API 라이브러리 로드

먼저 Google Maps API 라이브러리를 로드해야 합니다. 이 라이브러리는 지도를 웹 페이지에 삽입하고, 여러 기능을 사용할 수 있게 해줍니다.

### 2. 마커 생성

다음으로 마커를 생성합니다. 마커는 지도 상의 특정 위치를 표시하는 데 사용됩니다. 

```javascript
var marker = new google.maps.Marker({
  position: new google.maps.LatLng(latitude, longitude),
  map: map
});
```

### 3. 원 추가하기

마커가 생성되면, 그 주변에 원을 그릴 수 있습니다. Google Maps API에서는 `Circle` 객체를 사용하여 이를 수행할 수 있습니다.

```javascript
var circle = new google.maps.Circle({
  center: new google.maps.LatLng(latitude, longitude),
  radius: 1000, // 반지름을 미터 단위로 설정
  map: map
});
```

이렇게 하면 지정된 위치의 마커 주변에 원이 그려집니다.

## 마무리

Google Maps API는 지도에 핀을 추가하고, 그 주변에 원을 그리는 등 다양한 기능을 제공합니다. 위에서 설명한 방법을 따라하면, 원하는 위치에 마커와 원을 쉽게 추가할 수 있습니다. 이를 통해 지도를 더욱 정보로 만들고 사용자에게 유용한 데이터를 제공할 수 있습니다.