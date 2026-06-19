---
title: 폴더묶음 발행구조 테스트(실패)
date: 2026-06-19 14:00:00 +0900
categories: [Test, Structure]
tags: [mdchirp, jekyll, chirpy]
media_subpath: /assets/img/posts/2026-06-19-mdchirp-folder-test2026-06-19-mdchirp-folder-test/
description: _posts 하위에 글제목 폴더를 만들고 index.md와 이미지를 같은 폴더에 둬서 상대경로로 렌더되는지 검증하는 글.
pin: false
math: false
mermaid: false
toc: true
comments: true
image:
  path: cover.png
  alt: 커버 이미지 - 상대경로 테스트
---

## 이 글의 목적

이 글은 `mdchirp`가 채택하려는 **폴더묶음 발행구조**가 Chirpy 테마에서 실제로 동작하는지 확인하기 위한 테스트입니다.

구조는 다음과 같습니다.

```text
_posts/
└── 2026-06-19-mdchirp-folder-test/
    ├── index.md      ← 이 파일 (글 본문)
    ├── cover.png     ← 프론트매터 image.path 가 가리키는 커버
    └── sample.png    ← 본문에서 상대경로로 삽입하는 이미지
```

확인하려는 핵심 질문은 **"같은 폴더 안의 이미지를 상대경로(`sample.png`)로 참조했을 때 글에서 정상적으로 뜨는가?"** 입니다.

## 1. 상대경로 이미지 (가장 중요한 검증)

아래 이미지가 깨지지 않고 보이면 → **폴더묶음 방식 성공**.

![상대경로 이미지 테스트](sample.png)
_같은 폴더의 sample.png 를 상대경로로 삽입한 결과_

## 2. 이미지 크기 지정 (Chirpy 문법)

![크기 지정 이미지](sample.png){: w="400" h="300" }
_w / h 속성으로 크기 고정_

## 3. 이미지 정렬

![왼쪽 정렬](sample.png){: .left w="200" }

왼쪽 정렬 이미지 옆에 텍스트가 흐르는지 확인합니다. 이 문단은 이미지 오른쪽으로 감싸져야 합니다. Lorem ipsum dolor sit amet, consectetur adipiscing elit. 한글 문장도 함께 흘려서 줄바꿈이 자연스러운지 봅니다.

## 4. 프롬프트 박스

> 이건 info 프롬프트입니다.
{: .prompt-info }

> 이건 warning 프롬프트입니다.
{: .prompt-warning }

## 5. 코드블록 (파일명 + 언어)

```typescript
// 파일명 표시 + 문법 강조 테스트
interface Post {
  title: string
  markdown: string
}
```
{: file="src/types.ts" }

## 6. 인용 / 목록 / 링크

> 이것은 일반 인용문입니다. 발행 후 스타일이 정상 적용되는지 확인합니다.

- 순서 없는 목록 1
- 순서 없는 목록 2
  - 중첩 목록

1. 순서 있는 목록 1
2. 순서 있는 목록 2

[mdchirp 테스트 링크](https://chirpy.cotes.page/posts/write-a-new-post/)

## 7. 인라인 요소

본문 안에 `인라인 코드`, **굵게**, *기울임*, ~~취소선~~ 이 정상인지 확인합니다.

파일경로 강조: `/etc/hosts`{: .filepath }

---

## 체크리스트 (발행 후 눈으로 확인)

- [ ] 커버 이미지(cover.png)가 글 상단에 뜨는가
- [ ] 본문 상대경로 이미지(sample.png)가 깨지지 않는가
- [ ] 크기 지정 / 정렬이 적용되는가
- [ ] 프롬프트 박스 색상이 나오는가
- [ ] 코드블록 파일명이 상단에 표시되는가
- [ ] TOC(목차)가 우측에 생기는가

이 중 **두 번째 항목(상대경로 이미지)**이 가장 중요합니다. 이게 되면 mdchirp는 폴더묶음 구조를 표준으로 확정합니다.



결론: 실패 후 _posts/에 본문파일 직접 업로드 후 media subpath를 assets 내에 폴더를 만들어 지정하면 상대경로로 사용이 가능.
이 글은 그렇게 수정한 결과물임.
