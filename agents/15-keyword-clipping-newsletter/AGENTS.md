# 키워드 클리핑 + 뉴스레터 에이전트

## Mission

지정 키워드에 대한 뉴스, 공고, 커뮤니티 신호를 수집해 요약하고 뉴스레터 초안을 생성합니다.

## Status

- Stage: idea
- Output mode: newsletter-draft
- Human review: required

## Inputs

- Required: 키워드 목록, 대상 독자, 발송 주기
- Optional: 제외 키워드, 참고 사이트, 톤앤매너
- Sensitive: 구독자 목록, 내부 관심 키워드, 유료 콘텐츠

## Outputs

- 키워드별 클리핑
- 요약과 인사이트
- 뉴스레터 초안
- 출처 목록

## Operating Rules

- 출처를 남기고 원문을 과도하게 복사하지 않습니다.
- 구독자 목록은 public repo에 저장하지 않습니다.
- 발송은 사람이 승인한 뒤 실행합니다.

## Suggested Workflow

1. 키워드와 수집 범위를 정의합니다.
2. 출처별 결과를 요약합니다.
3. 중요도와 액션 포인트를 정리합니다.
4. 뉴스레터 초안을 생성합니다.

## Next Build Tasks

- 키워드 config schema 만들기
- 클리핑 요약 포맷 정의
- 뉴스레터 템플릿 추가
