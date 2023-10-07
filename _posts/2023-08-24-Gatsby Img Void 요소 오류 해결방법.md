---
title: Gatsby Img Void 요소 오류 해결방법
date: 2023-08-24 20:00:00 +0900
categories:
  - JavaScript
tags:
  - Gatsby
  - Img
  - Void요소오류
---

## 오류 개요

Gatsby 프로젝트에서 `gatsby-image` 라이브러리를 사용할 때 발생하는 일반적인 오류 중 하나는 "Gatsby Img is a void element tag and must neither have children nor use `dangerouslySetInnerHTML`"라는 메시지가 출력되는 것입니다. 이 오류는 `Img` 태그 안에 자식 요소나 `dangerouslySetInnerHTML` 속성을 사용하면 발생합니다.

## 오류 원인과 해결책

### 원인: Void Element 태그 사용

HTML에서는 `img`, `br`, `hr`과 같은 태그들을 'void element'라고 부릅니다. 이들 태그는 닫는 태그(`/`) 없이 단독으로 사용됩니다. `gatsby-image` 라이브러리의 `Img` 컴포넌트도 이러한 void element 중 하나로, 자식 요소나 `dangerouslySetInnerHTML` 속성을 포함할 수 없습니다.

### 해결책: 태그 수정

이 오류를 해결하기 위해서는 `Img` 태그 안에 다른 요소나 속성을 넣지 않는 것이 중요합니다. 아래와 같이 코드를 수정하면 오류를 해결할 수 있습니다.

```jsx
// 잘못된 예
<Img dangerouslySetInnerHTML={{ __html: 'some HTML' }} />

// 올바른 예
<Img fluid={data.someImage.childImageSharp.fluid} />
```

## 예방책: 코드 리뷰

이러한 오류는 코드 리뷰 과정에서도 쉽게 잡을 수 있습니다. 팀원과 코드를 공유하고, `Img` 태그가 올바르게 사용되었는지 확인하세요. 특히, JSX에서 `Img` 태그가 올바르게 닫혀있는지, 불필요한 속성이나 자식 요소가 없는지 확인하는 것이 좋습니다.

## 결론

'Gatsby Img is a void element tag and must neither have children nor use `dangerouslySetInnerHTML`' 오류는 `gatsby-image` 라이브러리의 `Img` 컴포넌트를 잘못 사용할 때 발생합니다. 이 오류를 방지하려면, `Img` 태그 안에 다른 요소나 속성을 넣지 않아야 합니다. 이러한 기본 규칙을 지키면, 이 오류를 쉽게 해결할 수 있습니다.