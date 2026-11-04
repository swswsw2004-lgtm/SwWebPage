---
title: "Hugo와 GitHub Actions로 개인 포트폴리오 사이트 만들기"
meta_title: ""
description: "초급프로젝트 과제로 진행한 개인 포트폴리오 사이트 제작 기록"
date: 2026-11-03T00:00:00+09:00
image: "/images/activity/portfolio-home-desktop.png"
categories: ["프로젝트"]
author: "안성우"
tags: ["Hugo", "GitHub Actions"]
draft: false
---

## 개요

- **기간:** 2026년 11월 ~ (진행 중)
- **형태:** 개인 과제 (2026학년도 초급프로젝트) · 모든 작업을 혼자 수행
- **사용 도구:** Hugo, Hugoplate 테마, Git/GitHub, GitHub Actions, GitHub Pages

## 목적

나를 소개하는 웹사이트를 직접 만들어 누구나 볼 수 있게 공개하고, Git으로 작업 과정을 기록하며 push만 하면 자동으로 배포되는 흐름을 처음부터 끝까지 경험하는 것이 목표였습니다.

## 내가 한 일

- Hugoplate 테마를 내려받아 GitHub 저장소에 올리고, 수업 제공 스크립트로 GitHub Pages 배포 워크플로를 설정했습니다.
- 사이트 제목, 언어(ko-kr), 시간대, 메뉴, GitHub 링크, 저작권 문구를 제 정보로 바꿨습니다.
- 가상 작성자·샘플 글·가짜 후기 같은 데모 콘텐츠를 지우고 소개와 활동 내용을 직접 작성했습니다.

## 진행 과정과 선택 이유

1. **테마 선택:** Hugoplate는 휴대폰·태블릿 화면에 맞춰지는 반응형 레이아웃이 기본으로 들어 있고, 소개 페이지와 글 목록 구조가 포트폴리오에 바로 쓸 수 있는 형태라 선택했습니다.
2. **배포 설정 충돌 해결:** 수업 스크립트를 실행하자 "기존 배포 워크플로가 있다"며 중단됐습니다. 원본 테마에 들어 있던 `.github/workflows/main.yml`이 원인이어서 이 파일을 삭제한 뒤 스크립트를 다시 실행했습니다.
3. **깨진 화면 해결:** 처음 배포된 사이트는 CSS와 이미지가 전혀 적용되지 않았습니다. 사이트가 `/SwWebPage/` 하위 경로에 있는데 원본 워크플로는 루트(`/`) 기준으로 빌드해서 파일 경로가 맞지 않았기 때문입니다. 수업 스크립트의 워크플로로 다시 배포해 해결했습니다.
4. **작은 단위로 커밋:** 설정 하나, 페이지 하나를 바꿀 때마다 커밋해서 무엇을 언제 바꿨는지 이력으로 남겼습니다.

## 결과

- 공개 사이트: [https://swswsw2004-lgtm.github.io/SwWebPage/](https://swswsw2004-lgtm.github.io/SwWebPage/)
- 저장소: [https://github.com/swswsw2004-lgtm/SwWebPage](https://github.com/swswsw2004-lgtm/SwWebPage)
- main 브랜치에 push하면 GitHub Actions가 자동으로 빌드·배포하고, 몇 분 뒤 공개 사이트에 반영됩니다.

![GitHub Actions에서 build와 deploy 단계가 모두 성공한 배포 실행 화면](/images/activity/portfolio-actions.png)

![390px 모바일 홈 화면, 왼쪽은 메뉴 닫힘·오른쪽은 메뉴 열림](/images/activity/portfolio-home-mobile.png)


## 배운 점과 개선 방향

- **배운 점:** 사이트 주소의 하위 경로(`/SwWebPage/`)와 빌드 설정(baseURL)이 맞지 않으면 CSS와 링크가 모두 깨진다는 것을 알게 되었습니다. 또 `git commit`만으로는 반영되지 않고 `git push`까지 해야 원격 저장소와 사이트가 바뀐다는 것을 직접 겪으며 이해했습니다.
- **한계와 다음 개선:** 아직 테마의 기본 디자인을 그대로 쓰고 있습니다. 다음에는 색상과 글꼴을 직접 바꿔 보고, Unity 게임 결과물을 이 사이트에 추가할 계획입니다.