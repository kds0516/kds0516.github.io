---
title: 워드프레스에 커스텀 페이지(CSS, JS, HTML, 이미지 포함) 추가하기
date: 2023-07-06 20:00:00 +0900
categories:
  - JavaScript
tags:
  - 워드프레스
---

## 소개
워드프레스는 사용이 간편하고 다양한 테마와 플러그인이 있어 많은 사람들이 선호하는 CMS(Content Management System, 콘텐츠 관리 시스템)입니다. 그러나 워드프레스로 만든 사이트에 자신만의 커스텀 페이지를 추가하고 싶을 때가 있습니다. 이 글에서는 CSS, JS, HTML, 그리고 이미지가 포함된 커스텀 페이지를 워드프레스에 어떻게 추가하는지에 대해 설명하겠습니다.

## 필요한 파일 준비
첫 번째로 해야 할 일은 커스텀 페이지를 구성할 파일을 준비하는 것입니다. HTML, CSS, JS 파일과 이미지를 워드프레스가 인식할 수 있는 디렉토리에 저장해야 합니다.

1. `wp-content/themes/your-theme/` 폴더에 HTML을 `custom-page.php`로 저장합니다.
2. `wp-content/themes/your-theme/css/` 폴더에 CSS를 저장합니다.
3. `wp-content/themes/your-theme/js/` 폴더에 JS를 저장합니다.
4. `wp-content/themes/your-theme/images/` 폴더에 이미지를 저장합니다.

## 커스텀 페이지 등록

워드프레스 대시보드에서 새 페이지를 만듭니다. 이때, 오른쪽 상단의 '페이지 속성'에서 '템플릿'을 `custom-page.php`로 설정합니다. 이렇게 하면 워드프레스가 이 파일을 커스텀 페이지로 인식하게 됩니다.

## 파일 연결하기
`custom-page.php` 파일 내에서 CSS와 JS를 불러오려면 `wp_enqueue_style`과 `wp_enqueue_script` 함수를 사용해야 합니다. 이는 워드프레스가 지원하는 공식 방법입니다.

```php
<?php
// CSS 연결
wp_enqueue_style('custom-page', get_template_directory_uri() . '/css/custom-page.css');

// JS 연결
wp_enqueue_script('custom-page', get_template_directory_uri() . '/js/custom-page.js');
?>
```

## HTML, CSS, JS 적용하기
마지막으로, `custom-page.php`에서 필요한 HTML, CSS, JS 코드를 추가합니다. 이 때, `wp_head()`와 `wp_footer()` 함수를 잊지 말고 넣어줍니다. 이 함수들은 워드프레스 테마에서 필수적인 기능을 로드하는 역할을 합니다.

## 주의사항
이 과정을 거친 후에도 페이지가 제대로 작동하지 않으면, 캐시를 비우고 다시 시도해 보세요. 또는, 개발자 도구를 사용해 오류를 확인하세요. 오류 메시지가 나타난다면 그대로 영어로 표시될 것입니다(예: `SyntaxError`, `TypeError` 등).

## 결론
이 글을 통해 워드프레스에 커스텀 페이지를 추가하는 방법을 알게 되었습니다. 이제 자신만의 독특한 웹 페이지를 워드프레스에 더해보세요.