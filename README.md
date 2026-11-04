# 안성우 개인 포트폴리오 사이트

웹 개발과 게임 개발에 관심 있는 안성우의 자기소개와 활동을 담은 개인 포트폴리오 사이트입니다.
2026학년도 초급프로젝트 과제 1로 제작했습니다.

- **공개 사이트:** https://swswsw2004-lgtm.github.io/SwWebPage/
- **저장소:** https://github.com/swswsw2004-lgtm/SwWebPage
- **배포 기록(Actions):** https://github.com/swswsw2004-lgtm/SwWebPage/actions

## 목차

1. [사이트 구성](#사이트-구성)
2. [폴더 구조와 수정할 파일](#폴더-구조와-수정할-파일)
3. [사용 도구와 버전](#사용-도구와-버전)
4. [설치 방법](#설치-방법)
5. [로컬에서 실행·빌드하기](#로컬에서-실행빌드하기)
6. [수정 후 재배포하기](#수정-후-재배포하기)
7. [출처와 라이선스](#출처와-라이선스)

## 사이트 구성

| 메뉴 | 주소 | 내용 |
|---|---|---|
| 홈 | `/SwWebPage/` | 한 줄 소개, 관심 분야·대표 활동 카드 |
| 소개 | `/SwWebPage/about/` | 관심 분야와 이유, 학습 목표와 실행 계획, 기술과 적용 사례 |
| 활동 | `/SwWebPage/blog/` | 활동 글 목록 |
| └ 대표 활동 | `/SwWebPage/blog/portfolio-site/` | 이 포트폴리오 사이트 제작 과정 |
| └ 추가 활동 | `/SwWebPage/blog/unity-2d-game/` | Unity 2D 게임 제작 경험 |
| 연락처 | `/SwWebPage/contact/` | 이메일, GitHub |

## 폴더 구조와 수정할 파일

실제 사이트는 **`site/` 폴더**로 빌드됩니다. `exampleSite/`와 저장소 최상위의 테마 파일은 원본 보관용이라 고쳐도 사이트에 반영되지 않습니다.

```text
SwWebPage/
├─ .github/
│  ├─ workflows/hugo-pages.yml   # GitHub Actions 배포 워크플로 (수업 스크립트가 생성)
│  └─ pages_build.py             # 의존성 설치·빌드 스크립트 (워크플로에서 사용)
├─ site/                         # ★ 실제 사이트 소스
│  ├─ hugo.toml                  # 사이트 제목, 시간대
│  ├─ pages.json                 # 배포 주소(baseURL) 등 배포용 설정 (수업 스크립트가 생성)
│  ├─ config/_default/
│  │  ├─ params.toml             # 로고 글자, 저작권, GitHub 버튼, 공지 배너
│  │  ├─ menus.en.toml           # 상단·하단 메뉴
│  │  └─ languages.toml          # 언어 설정 (ko-kr)
│  ├─ data/social.json           # 하단 소셜 링크 (GitHub)
│  ├─ content/english/
│  │  ├─ _index.md               # 홈 화면 배너·카드
│  │  ├─ about/_index.md         # 소개 페이지
│  │  ├─ blog/                   # 활동 글 (글 1개 = .md 파일 1개)
│  │  ├─ contact/_index.md       # 연락처 페이지
│  │  └─ sections/call-to-action.md  # 홈 하단 배너
│  ├─ assets/images/             # 사이트에서 쓰는 이미지
│  └─ themes/template/           # Hugoplate 테마 (수업 스크립트가 복사)
├─ exampleSite/                  # 원본 테마 예시 (사용하지 않음)
└─ prepare_github_pages.py       # 수업 제공 배포 준비 스크립트
```

**자주 고치는 곳**

- 글 내용을 바꾸려면 `site/content/english/` 안의 `.md` 파일을 고칩니다.
- 활동 글을 추가하려면 `site/content/english/blog/`에 새 `.md` 파일을 만듭니다. 파일 이름은 영어 소문자와 하이픈을 쓰고, `date`는 오늘 이전 날짜로 적습니다.
- 메뉴를 바꾸려면 `site/config/_default/menus.en.toml`을 고칩니다.
- 이미지를 추가하려면 `site/assets/images/`에 넣고 `/images/파일이름.png`로 참조합니다.

## 사용 도구와 버전

| 도구 | 버전 | 용도 |
|---|---|---|
| Hugo (extended) | 0.165.0 | 정적 사이트 생성 |
| Go | 1.27.1 (1.25 이상 필요) | Hugo 모듈 다운로드 |
| Node.js | 24 | Tailwind CSS 빌드 |
| Python | 3.12 (Actions) / 3.12.0 (로컬) | 배포 준비·빌드 스크립트 |
| Git | 2.55.0.windows.5 | 버전 관리 |

Actions에서 쓰는 버전은 `.github/workflows/hugo-pages.yml`에 고정되어 있습니다.

## 설치 방법

Windows 기준입니다. PowerShell 또는 Git Bash에서 실행합니다.

```bash
winget install Git.Git
winget install Python.Python.3.12
winget install OpenJS.NodeJS
winget install GoLang.Go
winget install Hugo.Hugo.Extended
```

설치 후 터미널을 다시 열고 버전을 확인합니다.

```bash
git --version
py --version
node --version
go version
hugo version     # 결과에 "extended"가 포함되어야 합니다
```

저장소를 내려받습니다.

```bash
git clone https://github.com/swswsw2004-lgtm/SwWebPage.git
cd SwWebPage
```

## 로컬에서 실행·빌드하기

**1. 의존성 설치** (처음 한 번)

```bash
py .github/pages_build.py --dependencies
```

**2. 미리보기 서버 실행** (수정하면 자동으로 새로고침됩니다)

```bash
cd site
hugo server --config hugo.toml,pages.json --theme template --themesDir themes
```

브라우저에서 http://localhost:1313/SwWebPage/ 를 엽니다. 종료하려면 `Ctrl+C`를 누릅니다.

**3. 배포용 빌드** (Actions와 같은 방식, 저장소 최상위 폴더에서 실행)

```bash
py .github/pages_build.py --build
```

결과물은 `public/` 폴더에 생성됩니다. 이 폴더는 `.gitignore`로 제외되어 커밋되지 않습니다.

## 수정 후 재배포하기

1. `site/` 안의 파일을 수정하고 저장합니다.
2. 커밋하고 main 브랜치에 push합니다.
   ```bash
   git add .
   git commit -m "수정 내용을 설명하는 메시지"
   git push
   ```
3. [Actions 탭](https://github.com/swswsw2004-lgtm/SwWebPage/actions)에서 **Deploy Hugo to GitHub Pages** 실행이 초록색(성공)이 될 때까지 기다립니다. 보통 1~3분 걸립니다.
4. 시크릿 창에서 https://swswsw2004-lgtm.github.io/SwWebPage/ 를 열어 변경 사항을 확인합니다. 예전 화면이 보이면 `Ctrl+Shift+R`로 새로고침하거나 몇 분 뒤 다시 엽니다.

GitHub Pages 설정은 **Settings → Pages → Build and deployment → Source: GitHub Actions**로 되어 있습니다.

## 출처와 라이선스

| 자료 | 사용 위치 | 구분 | 출처 | 이용 조건 |
|---|---|---|---|---|
| Hugoplate 테마 (레이아웃·CSS·JS) | `site/themes/template/`, `exampleSite/` | 외부 자료 | https://github.com/zeon-studio/hugoplate | MIT License (`LICENSE` 파일 유지, 사이트 하단에 출처 표기) |
| 홈 일러스트 (`banner.png`, `service-*.png`, `call-to-action.png`) | 홈 화면 | 외부 자료 (테마 포함) | Hugoplate 테마 | 테마와 동일 (MIT) |
| 배포 준비 스크립트 (`prepare_github_pages.py`, `.github/pages_build.py`, `hugo-pages.yml`) | 배포 | 외부 자료 (수업 제공) | 2026학년도 초급프로젝트 수업 | 수업 과제용 |
| 사이트 글 (소개·활동·연락처) | `site/content/english/` | 직접 작성 (AI 도움으로 초안 작성 후 직접 수정) | 본인 | - |
| 사이트 설정 변경 | `site/hugo.toml`, `site/config/_default/`, `site/data/social.json` | 직접 수정 | 본인 | - |
| 이 README | `README.md` | 직접 작성 (AI 도움으로 초안 작성 후 직접 수정) | 본인 | - |

AI 도구 사용 내역은 과제 보고서의 "AI 활용 기록"에 정리했습니다.
