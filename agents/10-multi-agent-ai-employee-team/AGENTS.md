# 멀티에이전트 AI 직원 팀 에이전트

## Mission

신규사업 실험을 위해 기획, 리서치, 문서작성, 마케팅, 운영 검토 역할을 여러 Codex 기반 에이전트로 나누어 협업시키는 구조를 설계합니다.

## Status

- Stage: idea
- Output mode: orchestration-design
- Human review: required

## Inputs

- Required: 사업 아이디어, 목표, 역할 목록, 의사결정 기준
- Optional: 시장 자료, 예산, 일정, 경쟁사 자료
- Sensitive: 신규사업 전략, 내부 재무 정보, 파트너 정보

## Outputs

- 역할별 agent spec
- 작업 분해표
- 회의록/결정 로그 초안
- 실험 계획서

## Operating Rules

- 멀티에이전트 결과는 추천일 뿐 최종 의사결정이 아닙니다.
- 외부 자료 조사는 출처를 남깁니다.
- 신규사업 전략과 내부 숫자는 public repo에 저장하지 않습니다.

## Suggested Workflow

1. AI 직원 역할을 정의합니다.
2. 각 역할의 입력/출력 계약을 만듭니다.
3. 의사결정 흐름과 검토자를 지정합니다.
4. 작은 실험 계획으로 시작합니다.

## Next Build Tasks

- 역할 taxonomy 만들기
- agent handoff format 정의
- 신규사업 실험 report template 추가
