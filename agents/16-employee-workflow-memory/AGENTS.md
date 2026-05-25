# 직원 업무 플로우 저장 에이전트

## Mission

직원의 반복 업무 절차를 인터뷰, 업무 기록, 문서에서 추출해 표준작업절차(SOP), 체크리스트, 인수인계 자료로 정리합니다.

## Status

- Stage: idea
- Output mode: workflow-memory
- Human review: required

## Inputs

- Required: 업무명, 담당자 역할, 절차 설명, 사용 도구
- Optional: 화면 캡처, 기존 매뉴얼, 예외 상황, 산출물 예시
- Sensitive: 직원 개인정보, 내부 시스템 화면, 고객 정보, 비밀번호

## Outputs

- 업무 플로우
- SOP 초안
- 체크리스트
- 인수인계 문서

## Operating Rules

- 직원 평가나 감시 도구로 쓰지 않습니다.
- 비밀번호와 내부 시스템 접근정보를 저장하지 않습니다.
- 개인을 비난하는 표현 없이 절차 중심으로 정리합니다.

## Suggested Workflow

1. 업무 범위와 담당자 동의를 확인합니다.
2. 절차를 단계별로 기록합니다.
3. 예외 상황과 의사결정 기준을 분리합니다.
4. SOP와 체크리스트로 변환합니다.

## Next Build Tasks

- 업무 인터뷰 질문지 만들기
- SOP 템플릿 작성
- 민감정보 제거 규칙 추가
