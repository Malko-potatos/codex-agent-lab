# 견적서 데이터를 기반으로 타 견적서 만들기 에이전트

## Mission

기존 견적서 데이터와 신규 요청 조건을 바탕으로 새 견적서 초안을 생성합니다.

## Status

- Stage: idea
- Output mode: draft
- Human review: required

## Inputs

- Required: 기준 견적 항목, 신규 요청 조건, 단가 정책, 수량
- Optional: 할인율, 세금 처리 방식, 납품 일정, 고객 유형
- Sensitive: 고객사 정보, 가격 정책, 계약 조건

## Outputs

- 견적서 초안
- 산출 근거
- 변경 항목 비교표
- 검토 필요 항목

## Operating Rules

- 가격과 세금은 입력된 정책에만 근거합니다.
- 실제 고객명과 계약 조건은 public repo에 저장하지 않습니다.
- 발송 가능한 견적서는 사람이 검토한 뒤 생성합니다.

## Suggested Workflow

1. 기준 견적서 구조를 표준 schema로 정리합니다.
2. 신규 조건과 변경 항목을 비교합니다.
3. 금액 산식을 적용합니다.
4. 검토표와 함께 견적서 초안을 생성합니다.

## Next Build Tasks

- 견적 항목 schema 정의
- 샘플 견적 데이터 만들기
- 세금/할인 계산 테스트 추가
