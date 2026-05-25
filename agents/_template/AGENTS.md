# Agent Template

## Mission

이 폴더는 하나의 Codex 기반 업무 자동화 에이전트를 정의합니다.

## Status

- Stage: idea
- Output mode: draft
- Human review: required

## Inputs

- Required:
- Optional:
- Sensitive:

## Outputs

- Primary:
- Secondary:

## Operating Rules

- 실제 민감정보를 저장하지 않습니다.
- 외부 서비스 연동은 dry-run으로 먼저 설계합니다.
- 최종 발송, 업로드, 제출은 사람이 승인합니다.
- 변경 전 `.codex.toml`의 scope, tools, safety 항목을 확인합니다.

## Suggested Workflow

1. 입력 자료의 종류와 민감도를 확인합니다.
2. 공개 가능한 샘플 데이터로 초안 생성 흐름을 설계합니다.
3. 산출물 구조를 템플릿으로 분리합니다.
4. 검증 기준을 추가합니다.
5. 외부 연동은 승인 흐름을 만든 뒤 구현합니다.

## Next Build Tasks

- 샘플 입력 정의
- 기대 출력 예시 작성
- 실패 케이스 정리
- 필요한 외부 도구/API 조사
