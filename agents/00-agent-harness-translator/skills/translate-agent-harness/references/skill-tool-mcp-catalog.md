# Skill, 도구, MCP 선택 카탈로그

이 문서는 0번 에이전트 하네스 번역기가 수강생에게 골라줄 수 있는 skill, 도구, MCP 후보를 정리한 참조 문서입니다.

쉽게 말해 이 문서는 “이 업무를 만들 때 어떤 재료를 고르면 좋을까요?”에 답하기 위한 메뉴판입니다. 0번 에이전트는 새 업무 아이디어를 하네스로 번역할 때 이 문서를 보고 필요한 후보만 골라야 합니다.

## 먼저 기억할 점

- 처음부터 많은 도구를 고르지 않습니다. 요구사항이 부족한 상태에서는 local draft, mock data, 사람 검토로 시작합니다.
- 외부 서비스 연결은 읽기 전용과 dry-run부터 검토합니다.
- 메시지 발송, 파일 업로드, 게시, 제출, 로그인 세션 사용은 사람 승인이 필요합니다.
- 수업 repo에는 실제 고객 자료, 회사 원문, 토큰, 쿠키, 비밀번호를 넣지 않습니다.
- 이 문서는 시작 목록입니다. 새 도구를 발견하면 출처와 용도를 확인한 뒤 추가합니다.

## 선택 기준

| 질문 | 고를 후보 |
|------|-----------|
| 문서 작성 순서나 검토 절차가 필요합니다. | skill |
| 파일을 만들거나 로컬에서 검증해야 합니다. | Codex 내장 도구 |
| 웹사이트, 이메일, 캘린더, Drive 같은 외부 서비스와 연결해야 합니다. | MCP 또는 connector |
| HWP/HWPX 문서를 열어 보고 PDF로 내보내는 흐름이 필요합니다. | HOP |
| 최신 OpenAI API나 Codex 공식 문서가 필요합니다. | `openai-docs` skill |

## Codex 내장으로 시작하는 후보

아래 항목은 이 스터디에서 먼저 고려할 수 있는 기본 재료입니다.

| 후보 | 쉬운 설명 | 부족한 상태에서의 사용법 | 주의할 점 |
|------|-----------|----------------|-----------|
| 로컬 파일 읽기/쓰기 | 내 컴퓨터 안의 파일을 보고 문서를 만듭니다. | mock markdown, JSON, HTML 파일 생성 | 실제 고객 자료는 저장하지 않습니다. |
| shell 명령 | 파일 목록 확인, TOML 검증, git 상태 확인 같은 작업을 합니다. | `git status`, TOML 파싱, 텍스트 검색 | 삭제/초기화 명령은 사용하지 않습니다. |
| 브라우저 확인 | 만든 HTML 화면이나 웹 흐름을 눈으로 확인합니다. | 행사 홈페이지 초안 미리보기 | 로그인된 외부 사이트는 별도 승인이 필요합니다. |
| 이미지 생성 | 수업용 예시 이미지, 더미 비주얼을 만듭니다. | 실제 사진 대신 샘플 이미지 생성 | 실제 인물/고객 사진 대체용으로만 사용합니다. |
| 문서/스프레드시트/프레젠테이션 도구 | `.docx`, `.xlsx`, `.pptx` 같은 업무 산출물을 다룹니다. | 요구사항이 보강된 뒤 변환 후보로 검토 | 부족한 상태에서는 markdown/json 초안부터 시작합니다. |
| Git/GitHub | 변경 기록을 남기고 원격 저장소에 올립니다. | 수업 자료 변경 commit/push | 민감 파일이 섞였는지 먼저 확인합니다. |

## HWP/HWPX 후보: HOP

| 항목 | 내용 |
|------|------|
| 후보 | HOP |
| 출처 | https://github.com/golbin/hop |
| 쉬운 설명 | HWP/HWPX 문서를 열어 보고, 저장하고, PDF로 내보낼 수 있는 오픈소스 데스크탑 앱입니다. |
| 언제 고릅니다 | 사업계획서, 공문, 지원사업 서류처럼 한글 문서 확인 흐름이 필요할 때 고릅니다. |
| 부족한 상태에서의 사용법 | 실제 `.hwp` 자동 생성은 하지 않고, “나중에 HWP 확인/내보내기 후보”로만 기록합니다. |
| 주의할 점 | 실제 회사 문서 원문은 repo에 넣지 않습니다. HOP는 문서 확인 도구 후보이지, 민감 문서를 공개 저장소에 저장해도 된다는 뜻이 아닙니다. |

HOP README 기준으로 HOP는 HWP/HWPX 문서를 보고 편집할 수 있는 macOS, Windows, Linux용 오픈소스 데스크탑 앱이며, HWP/HWPX 열기, HWP 저장, PDF 내보내기, 인쇄, 파일 연결 등을 지원합니다.

## OpenAI system skills

OpenAI skills repo 기준으로 `.system` skills는 최신 Codex에 자동 설치되는 기본 skill입니다.

| skill | 쉬운 설명 | 수업에서 고르는 경우 |
|-------|-----------|---------------------|
| `imagegen` | 이미지를 만들거나 수정합니다. | 더미 비주얼, 샘플 이미지, 행사 이미지 초안이 필요할 때 |
| `openai-docs` | OpenAI/Codex 공식 문서를 찾아 확인합니다. | OpenAI API, Codex 기능, 모델 선택 기준이 필요할 때 |
| `plugin-creator` | Codex plugin 뼈대를 만듭니다. | 수업 후반에 새 plugin 구조를 만들 때 |
| `skill-creator` | 새 skill을 만드는 방법을 안내합니다. | 반복 절차를 수업용 skill로 분리할 때 |
| `skill-installer` | curated skill이나 외부 skill을 설치합니다. | OpenAI curated skill을 추가로 설치할 때 |

## OpenAI curated skills

OpenAI skills repo 기준으로 `.curated` skills는 필요할 때 설치해서 쓸 수 있는 후보입니다. 0번 에이전트는 아래 목록을 보고 업무에 맞는 후보만 추천합니다.

### 문서, PDF, 노트북, 음성

| skill | 쉬운 설명 | 수업에서 고르는 경우 |
|-------|-----------|---------------------|
| `pdf` | PDF를 읽고 만들고 검토합니다. | 공고문, 보고서, 제출서류 PDF를 다룰 때 |
| `jupyter-notebook` | 실험용 노트북을 만듭니다. | 데이터 분석 실습 노트를 만들 때 |
| `speech` | 텍스트를 음성으로 읽어주는 파일을 만듭니다. | 안내 음성, 내레이션 초안이 필요할 때 |
| `transcribe` | 녹음 파일을 글로 풀어 줍니다. | 인터뷰, 회의 녹취를 요약하기 전에 |
| `screenshot` | 화면 캡처를 다룹니다. | UI나 결과 화면을 증빙으로 남길 때 |

### 웹사이트와 배포

| skill | 쉬운 설명 | 수업에서 고르는 경우 |
|-------|-----------|---------------------|
| `playwright` | 브라우저를 자동으로 열고 화면을 검증합니다. | 행사 홈페이지 초안을 확인할 때 |
| `playwright-interactive` | 브라우저를 반복해서 조작하며 디버깅합니다. | UI 확인을 여러 번 해야 할 때 |
| `netlify-deploy` | Netlify에 웹사이트를 배포합니다. | 수업 후반에 preview 배포를 할 때 |
| `vercel-deploy` | Vercel에 웹사이트를 배포합니다. | 프론트엔드 preview 배포가 필요할 때 |
| `render-deploy` | Render에 앱을 배포합니다. | 서버 앱 배포 후보가 필요할 때 |
| `cloudflare-deploy` | Cloudflare Workers/Pages를 다룹니다. | Cloudflare 기반 배포가 필요할 때 |

### GitHub와 개발 흐름

| skill | 쉬운 설명 | 수업에서 고르는 경우 |
|-------|-----------|---------------------|
| `yeet` | 변경 내용을 commit, push, PR까지 이어갑니다. | 수업 자료를 GitHub에 올릴 때 |
| `gh-address-comments` | GitHub PR 리뷰 댓글을 처리합니다. | 리뷰 반영 실습을 할 때 |
| `gh-fix-ci` | GitHub Actions 실패를 확인하고 고칩니다. | CI 실패 원인을 찾을 때 |
| `migrate-to-codex` | 기존 설정을 Codex 방식으로 옮깁니다. | 다른 repo를 Codex 수업 구조로 옮길 때 |
| `cli-creator` | CLI 도구를 만듭니다. | 반복 작업을 명령어로 만들 때 |

### 디자인과 Figma

| skill | 쉬운 설명 | 수업에서 고르는 경우 |
|-------|-----------|---------------------|
| `figma` | Figma 파일을 읽고 디자인 정보를 가져옵니다. | Figma 기반 화면 구현을 할 때 |
| `figma-use` | Figma 도구를 쓰기 전 필수 준비 skill입니다. | Figma 도구 호출 전 |
| `figma-implement-design` | Figma 디자인을 코드로 구현합니다. | 디자인 시안을 웹 화면으로 옮길 때 |
| `figma-generate-design` | 코드나 페이지를 Figma 디자인으로 만듭니다. | 만든 화면을 Figma로 정리할 때 |
| `figma-generate-library` | Figma 디자인 시스템을 만듭니다. | 반복 UI 규칙을 만들 때 |
| `figma-create-new-file` | 새 Figma 파일을 만듭니다. | 디자인 파일을 새로 시작할 때 |
| `figma-create-design-system-rules` | 프로젝트용 디자인 규칙을 만듭니다. | 수업용 UI 규칙을 정할 때 |
| `figma-code-connect-components` | Figma 컴포넌트와 코드 컴포넌트를 연결합니다. | 디자인과 코드 매핑이 필요할 때 |

### Notion, Linear, Sentry

| skill | 쉬운 설명 | 수업에서 고르는 경우 |
|-------|-----------|---------------------|
| `notion-knowledge-capture` | 대화와 결정을 Notion 문서로 정리합니다. | 수업 기록을 Notion에 남길 때 |
| `notion-meeting-intelligence` | Notion 자료로 회의 준비를 합니다. | 회의 agenda, pre-read가 필요할 때 |
| `notion-research-documentation` | Notion 자료를 모아 리서치 문서를 만듭니다. | 여러 노트를 한 문서로 정리할 때 |
| `notion-spec-to-implementation` | Notion 기획서를 구현 계획으로 바꿉니다. | 기획서를 작업 목록으로 나눌 때 |
| `linear` | Linear 이슈와 프로젝트를 다룹니다. | Linear로 업무 티켓을 관리할 때 |
| `sentry` | Sentry 오류를 확인합니다. | 운영 오류를 읽고 요약할 때 |

### OpenAI, 앱, 프레임워크, 보안

| skill | 쉬운 설명 | 수업에서 고르는 경우 |
|-------|-----------|---------------------|
| `openai-docs` | OpenAI 공식 문서를 확인합니다. | API나 모델 사용법을 확인할 때 |
| `chatgpt-apps` | ChatGPT 앱을 만듭니다. | MCP server와 UI를 연결하는 앱을 만들 때 |
| `aspnet-core` | ASP.NET Core 앱을 다룹니다. | .NET 웹앱 수업이나 업무가 있을 때 |
| `winui-app` | Windows 데스크탑 앱을 만듭니다. | Windows 앱 실습이 필요할 때 |
| `security-best-practices` | 보안 모범 사례를 검토합니다. | 코드나 설계의 보안 기본기를 확인할 때 |
| `security-threat-model` | 위협 모델을 만듭니다. | 어떤 공격이나 위험이 있는지 정리할 때 |
| `security-ownership-map` | 보안 책임 영역을 분석합니다. | 큰 코드베이스의 책임자를 파악할 때 |
| `define-goal` | 흐릿한 목표를 측정 가능한 목표로 바꿉니다. | 수강생의 목표가 아직 모호할 때 |
| `hatch-pet` | Codex pet sprite/애니메이션을 만듭니다. | 수업용 재미 요소나 캐릭터가 필요할 때 |

## MCP 또는 외부 서비스 후보

아래 후보는 실제 계정, 로그인, API 권한이 필요할 수 있습니다. 요구사항이 부족한 상태에서는 대부분 mock data 또는 dry-run으로만 다룹니다.

| 외부 서비스 | 쉬운 설명 | 첫 추천 방식 | 승인 필요 지점 |
|-------------|-----------|--------------|----------------|
| GitHub | 코드와 문서 변경을 관리합니다. | commit/push 실습 | 민감 파일 포함 여부 확인 |
| Google Drive / Docs / Sheets / Slides | 회사 문서, 표, 발표자료를 다룹니다. | 샘플 문서로 구조 확인 | 실제 회사 문서 접근 |
| Google Calendar | 일정과 회의 정보를 다룹니다. | mock 일정으로 daily brief 설계 | 실제 캘린더 읽기/수정 |
| Gmail | 이메일을 읽고 답장 초안을 만듭니다. | 이메일 초안만 작성 | 실제 발송 |
| Netlify / Vercel / Render / Cloudflare | 웹사이트나 앱을 배포합니다. | preview 배포 후보로만 기록 | 실제 배포 |
| Figma | 디자인 파일을 읽고 화면 구현에 활용합니다. | 공개 또는 샘플 디자인 사용 | 실제 고객 디자인 접근 |
| Notion / Linear / Sentry | 지식관리, 업무관리, 오류관리를 합니다. | mock 업무 흐름으로 시작 | 실제 workspace 접근 |
| 네이버웍스 | 메일, 캘린더, 메시지, 파일을 다룹니다. | 부족한 상태에서는 후보로만 기록 | 로그인, 메시지, 파일 접근 |
| 네이버카페 | 커뮤니티 글을 분석합니다. | mock 게시글 분석부터 시작 | 로그인 세션, 크롤링, 원문 저장 |

## 0번 에이전트가 추천할 때 쓰는 말

0번 에이전트는 수강생에게 아래 순서로 설명합니다.

1. 이 업무에 필요한 후보를 2-3개만 고릅니다.
2. 왜 골랐는지 쉬운 말로 설명합니다.
3. 부족한 상태에서는 무엇을 하지 않을지 함께 적습니다.
4. 외부 서비스가 있으면 승인 지점을 적습니다.
5. 민감정보가 들어가면 mock data로 바꾸라고 안내합니다.

예시:

```text
이 업무에는 `pdf` skill과 로컬 파일 생성 도구만 먼저 고르면 됩니다.
Google Drive 연동은 실제 회사 문서를 읽어야 하므로 부족한 상태에서는 제외합니다.
먼저 더미 공고문 PDF와 markdown 검토표로 흐름을 검증합니다.
```

## 출처와 갱신 기준

- HOP: https://github.com/golbin/hop
- OpenAI skills README: https://github.com/openai/skills
- OpenAI curated skills: https://github.com/openai/skills/tree/main/skills/.curated
- OpenAI system skills: https://github.com/openai/skills/tree/main/skills/.system

이 목록은 2026-05-26에 확인한 내용으로 시작합니다. skill이나 외부 서비스는 바뀔 수 있으므로, 수업 전에는 출처 링크를 다시 확인합니다.
