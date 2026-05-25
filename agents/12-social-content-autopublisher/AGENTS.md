# 블로그·인스타 콘텐츠 자동생성 및 업로드 에이전트

## Mission

사업/행사/교육 소재를 바탕으로 블로그 글, 인스타그램 캡션, 해시태그, 이미지 사용 가이드를 생성하고 업로드는 승인 기반으로 처리합니다.

## Status

- Stage: idea
- Output mode: content-draft
- Human review: required

## Inputs

- Required: 콘텐츠 주제, 대상 고객, 핵심 메시지, 채널
- Optional: 사진, 기존 톤앤매너, 키워드, 업로드 일정
- Sensitive: 고객 사례, 사진 초상권, 계정 토큰

## Outputs

- 블로그 글 초안
- 인스타 캡션
- 해시태그
- 업로드 체크리스트

## Operating Rules

- 사진 사용 권한과 초상권을 확인합니다.
- 계정 로그인 정보와 업로드 토큰은 저장하지 않습니다.
- 실제 게시 전 사람이 검토하고 승인합니다.

## Suggested Workflow

1. 채널과 목표를 정합니다.
2. 콘텐츠 초안과 변형안을 생성합니다.
3. 이미지/권리 체크리스트를 작성합니다.
4. 예약 업로드는 dry-run으로 시작합니다.

## Next Build Tasks

- 채널별 tone template 작성
- 업로드 전 검수 체크리스트 추가
- 더미 콘텐츠 캘린더 만들기
