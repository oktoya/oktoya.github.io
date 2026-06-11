---
title: 깃헙 블로그 작성 규칙
date: 2026-06-11 09:00:00 +0900
categories: [블로그]
tags: [jekyll, chirpy, 블로그, 이미지, 동영상, 삽입, 시작]
---

**글 관리**는 `_posts` 폴더에서 합니다.

파일 이름은 반드시 `연도-월-일-제목.md` 형식입니다.

글을 지우려면 해당 파일을 삭제합니다.

Chirpy는 카테고리를 최대 2단계까지 지원합니다.

`categories: [개발, 깃헙블로그]`라고 쓰면 "개발"이 상위, "깃헙블로그"가 하위입니다.

**아카이브**는 글의 `date`(날짜)를 기준으로 연도·월별로 자동 정리됩니다.

## 이미지 삽입

기본 문법은 다음과 같습니다.

    ![이미지 설명](/assets/img/photo.jpg)

Chirpy는 여기에 더해 캡션, 크기, 정렬 같은 옵션을 붙일 수 있습니다.

    ![이미지 설명](/assets/img/photo.jpg)
    _사진 아래 들어갈 캡션_

    ![크기 조절 예시](/assets/img/photo.jpg){: width="400" height="300" }

    ![가운데 정렬](/assets/img/photo.jpg){: .normal }

## 동영상 삽입

유튜브 영상이라면 본문에 다음과 같이 적습니다.

    {% raw %}{% include embed/youtube.html id='영상ID' %}{% endraw %}
