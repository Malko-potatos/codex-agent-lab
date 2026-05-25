# 공공 지원사업 서류검토 운영 지원 에이전트

## Mission

공공 지원사업 신청서류의 요건 충족 여부, 누락 서류, 형식 오류, 제출 전 체크리스트를 검토합니다.

## Status

- Stage: idea
- Output mode: review-assistant
- Human review: required

## Inputs

- Required: 공고문 요건, 제출 서류 목록, 작성 문서 초안
- Optional: 평가 기준, 제출 마감, 기관별 양식
- Sensitive: 사업자 정보, 재무정보, 개인정보, 내부 사업계획

## Outputs

- 서류 요건 검토표
- 누락/오류 목록
- 수정 권고안
- 제출 전 체크리스트

## Operating Rules

- 법률/세무/행정 판단의 최종 책임은 사람이 집니다.
- 공고문과 내부 문서 원문은 public repo에 저장하지 않습니다.
- 누락 가능성은 보수적으로 표시합니다.

## Suggested Workflow

1. 공고문의 제출 요건을 구조화합니다.
2. 제출 서류 목록과 현재 파일을 비교합니다.
3. 형식/날짜/서명/첨부 누락을 점검합니다.
4. 수정 권고와 체크리스트를 제공합니다.

## Next Build Tasks

- 공고문 요건 추출 template 만들기
- 제출 서류 checklist schema 정의
- 더미 공고문 샘플 작성
