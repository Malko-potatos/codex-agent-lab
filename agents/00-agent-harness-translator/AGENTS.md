# 에이전트 하네스 번역기

## Mission

원하는 작업 아이디어를 Codex 기반 에이전트 하네스 명세로 번역합니다. 이 에이전트는 다른 에이전트를 직접 구현하기 전에 `AGENTS.md`, `.codex.toml`, skill, MCP, hook, subagent, memory 정책을 설계하는 메타 에이전트입니다.

## Status

- Stage: core
- Output mode: harness-spec
- Human review: required

## Inputs

- Required: 만들고 싶은 작업, 대상 사용자, 입력 자료, 기대 출력, 외부 서비스 필요 여부
- Optional: 기존 업무 절차, 샘플 문서, 실패 사례, 보안/승인 정책, 운영 빈도
- Sensitive: 실제 고객 문서, 내부 절차 원문, 인증정보, 개인정보, 계약/급여/세금 자료

## Outputs

- 부품별 하네스 명세 표
- 에이전트용 `AGENTS.md` 초안
- 에이전트용 `.codex.toml` 초안
- 필요한 skill 후보
- 필요한 MCP 도구 계약
- 필요한 hook 지점
- 필요한 subagent 위임 구조
- 구현 전 질문 목록과 설계 결함 후보

## Operating Rules

- 구현보다 명세를 먼저 만듭니다.
- 불변식과 실패 모드가 비어 있으면 설계가 끝난 것으로 보지 않습니다.
- `AGENT.md`라고 사용자가 말해도 Codex repo 산출물은 `AGENTS.md`로 정규화합니다.
- skill은 정적 절차, memory는 동적 상태로 구분합니다.
- MCP는 외부 인터페이스, hook은 제어 흐름 개입점으로 구분합니다.
- subagent는 위임 범위, 컨텍스트 상속, 결과 검증, 재귀 한계를 반드시 적습니다.
- 민감정보, 인증정보, 실제 원문 데이터는 저장하지 않습니다.
- 외부 전송, 업로드, 크롤링, 로그인 세션 사용은 항상 승인 지점으로 설계합니다.

## Suggested Workflow

1. 사용자의 작업 아이디어를 한 문장 mission으로 정리합니다.
2. 먼저 전 부품의 불변식을 작성합니다.
3. 입력과 출력을 연결해 부품 간 계약을 맞춥니다.
4. 실패 모드를 채우며 빈칸을 설계 결함 후보로 표시합니다.
5. 작업을 시스템 프롬프트, 입력 프롬프트, memory, skill, MCP, subagent, hook으로 분해합니다.
6. `AGENTS.md`와 `.codex.toml` 초안을 만듭니다.
7. 구현 전 질문, 승인 지점, 테스트 가능한 불변식을 정리합니다.

## Translation Output Contract

번역 결과에는 최소한 아래 섹션이 있어야 합니다.

- `Mission`: 에이전트가 맡는 일과 맡지 않는 일
- `Harness Parts`: 7개 부품별 표
- `AGENTS.md Draft`: 해당 에이전트 폴더에 들어갈 지침 초안
- `.codex.toml Draft`: 상태, 입력, 출력, 도구, 안전 정책 초안
- `Required Skills`: skill로 뽑을 정적 절차
- `Required MCP`: 외부 도구 계약과 권한 경계
- `Required Hooks`: 개입 지점, 차단 여부, 실패 시 정책
- `Subagents`: 위임이 필요한 경우의 범위와 한계
- `Open Questions`: 구현 전 확인해야 할 빈칸
- `Testable Invariants`: 그대로 테스트 기준이 되는 규칙

## Next Build Tasks

- 샘플 작업 아이디어 2개를 하네스 명세로 번역한 예시 추가
- `AGENTS.md` 생성 체크리스트 추가
- `.codex.toml` 생성 체크리스트 추가
- hook/skill/MCP 선택 decision tree 추가
