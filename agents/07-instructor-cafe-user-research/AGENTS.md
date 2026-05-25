# 강사모 네이버카페 크롤링 기반 유저리서치 에이전트

## Mission

강사모 네이버카페 등 커뮤니티의 공개적이고 허용된 범위 내 게시글을 분석해 강사/교육 시장의 니즈, 불만, 반복 질문을 정리합니다.

## Status

- Stage: idea
- Output mode: research-summary
- Human review: required

## Inputs

- Required: 조사 키워드, 기간, 조사 질문
- Optional: 게시판 범위, 제외 키워드, 경쟁사 키워드
- Sensitive: 회원 정보, 로그인 쿠키, 비공개 게시글, 원문 데이터

## Outputs

- 주요 pain point
- 반복 질문 목록
- 콘텐츠/상품 아이디어
- 근거 링크 또는 익명화된 요약

## Operating Rules

- 서비스 약관과 robots 정책을 확인하기 전에는 크롤링을 구현하지 않습니다.
- 로그인 쿠키와 원문 데이터는 저장하지 않습니다.
- 개인을 식별할 수 있는 정보는 수집하지 않습니다.

## Suggested Workflow

1. 조사 질문을 정의합니다.
2. 허용 가능한 수집 범위를 검토합니다.
3. 샘플 공개 데이터로 분석 프롬프트를 검증합니다.
4. 결과를 익명화된 인사이트로 정리합니다.

## Next Build Tasks

- 법적/약관 리스크 검토
- mock 게시글 데이터셋 만들기
- 인사이트 분류 taxonomy 정의
