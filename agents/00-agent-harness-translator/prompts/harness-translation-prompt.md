# Harness Translation Prompt

사용자의 자연어 업무 아이디어를 Codex 기반 에이전트 하네스 명세로 번역한다.

## 입력

- 만들고 싶은 작업
- 대상 사용자
- 입력 자료
- 기대 출력
- 외부 서비스 여부
- 보안/승인 제약

## 출력 순서

1. 작업 mission을 한 문장으로 요약한다.
2. 맡는 일과 맡지 않는 일을 분리한다.
3. 불변식을 먼저 작성한다.
4. 공식 Codex memory, `AGENTS.md`, checked-in docs, skill의 경계를 먼저 나눈다.
5. 시스템 프롬프트, 입력 프롬프트, 메모리, skill, MCP, subagent, hook 표를 채운다.
6. 빈칸을 설계 결함 후보로 표시한다.
7. `AGENTS.md` 초안을 작성한다.
8. `.codex.toml` 초안을 작성한다.
9. 구현 전 질문과 테스트 가능한 불변식을 정리한다.

## 번역 규칙

- `AGENT.md`라는 표현은 Codex 산출물에서는 `AGENTS.md`로 정규화한다.
- skill은 반복 가능한 정적 절차다.
- memory는 작업 중 또는 작업 간 보존되는 동적 상태다.
- Codex 공식 memory는 repo 안 `MEMORY.md`가 아니라 Codex home의 `~/.codex/memories/` 아래 생성되는 local recall layer로 다룬다.
- 반드시 지켜야 하는 팀 규칙과 보안 정책은 memory가 아니라 `AGENTS.md` 또는 checked-in docs에 둔다.
- memory 항목에는 기억 목적, 기억 후보, 저장 금지 데이터, 저장 위치, 저장 시점, 사용 시점, thread control, 검토/삭제 방법을 적는다.
- memory는 즉시 저장된다고 가정하지 않는다. Codex는 eligible thread가 idle 상태가 된 뒤 background로 memory를 만들 수 있다.
- MCP는 외부 시스템과 연결되는 능력이다.
- hook은 실행 흐름 중 특정 지점에 개입하는 제어 장치다.
- subagent는 위임 가능한 별도 작업자이며 재귀 한계가 필요하다.
- 실패 모드가 없는 부품은 미완성이다.
- 불변식이 없는 부품은 테스트 기준이 없는 것이다.
- 외부 전송, 업로드, 크롤링, 로그인 세션 사용은 승인 지점을 요구한다.
- public repo에는 실제 데이터, 비밀키, 원문 문서, 개인정보를 넣지 않는다.
