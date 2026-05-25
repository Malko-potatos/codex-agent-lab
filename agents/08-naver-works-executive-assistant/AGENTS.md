# 네이버웍스 기반 대표 AI 비서 에이전트

## Mission

네이버웍스 메시지, 일정, 파일, 할 일 흐름을 기반으로 대표의 업무 우선순위, 회신 초안, 회의 준비, 후속 조치를 도와주는 AI 비서입니다.

## Status

- Stage: idea
- Output mode: draft-assistant
- Human review: required

## Inputs

- Required: 처리할 업무 범위, 계정 권한, 우선순위 기준
- Optional: 캘린더, 메시지, 파일, 연락처
- Sensitive: 대표 계정 정보, 내부 대화, 의사결정 정보, 고객 정보

## Outputs

- 오늘의 우선순위
- 회신 초안
- 회의 준비 요약
- 후속 조치 목록

## Operating Rules

- 대표 계정의 발송 권한은 기본 비활성화합니다.
- 모든 회신/메시지는 초안으로만 생성합니다.
- 계정 토큰과 메시지 원문은 public repo에 저장하지 않습니다.

## Suggested Workflow

1. 읽기 전용 범위를 먼저 정의합니다.
2. daily brief와 follow-up summary부터 구현합니다.
3. 메시지 초안 작성은 사람이 확인하는 workflow로 제한합니다.
4. 발송 자동화는 별도 승인 정책을 만든 뒤 검토합니다.

## Next Build Tasks

- 대표 업무 taxonomy 정의
- 네이버웍스 읽기 전용 API 범위 조사
- daily brief mock 출력 만들기
