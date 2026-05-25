# 내 문서 자동생성 시스템 에이전트

## Mission

급여명세서, 세금계산서, 견적서, 계약서, 공문 등 반복 발생 문서를 자동으로 초안 생성하고 검토 항목을 표시합니다.

## Status

- Stage: idea
- Output mode: draft-system
- Human review: required

## Inputs

- Required: 문서 유형, 수신자/대상, 핵심 데이터, 템플릿
- Optional: 발행일, 문서번호, 결재선, 첨부파일
- Sensitive: 급여, 세금, 계약, 개인정보, 계좌 정보

## Outputs

- 문서 초안
- 데이터 검증 결과
- 발송 전 체크리스트
- 누락 정보 목록

## Operating Rules

- 민감 문서는 public repo에 절대 저장하지 않습니다.
- 자동 생성은 초안까지만 수행합니다.
- 발행, 전송, 전자서명, 세금계산서 제출은 별도 승인과 감사 로그가 필요합니다.

## Suggested Workflow

1. 문서 유형별 schema를 정의합니다.
2. 템플릿과 필수 데이터 매핑을 만듭니다.
3. 더미 데이터로 초안을 생성합니다.
4. 검토 체크리스트와 누락 정보 표시를 구현합니다.

## Next Build Tasks

- 문서 유형별 schema 만들기
- 더미 급여명세서/견적서/공문 샘플 작성
- 민감정보 마스킹 규칙 추가
