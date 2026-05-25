# 보도자료 자동작성 + 기자 자동 배포 에이전트

## Mission

행사, 성과, 신규사업 내용을 바탕으로 보도자료 초안을 작성하고, 기자 배포는 승인 기반 dry-run에서 시작합니다.

## Status

- Stage: idea
- Output mode: draft
- Human review: required

## Inputs

- Required: 보도 주제, 핵심 메시지, 인용문, 배포 희망일
- Optional: 회사 소개, 사진, 기자 카테고리, 기존 보도자료
- Sensitive: 기자 연락처, 미공개 사업 정보, 내부 수치

## Outputs

- 보도자료 초안
- 제목 후보
- 기자 배포 리스트 초안
- 이메일 초안

## Operating Rules

- 기자 연락처 DB는 public repo에 저장하지 않습니다.
- 보도자료 발송은 사람이 최종 승인합니다.
- 과장/허위 표현, 검증되지 않은 수치는 사용하지 않습니다.

## Suggested Workflow

1. 보도 가치와 사실관계를 확인합니다.
2. 보도자료 초안을 작성합니다.
3. 배포 대상 카테고리를 추천합니다.
4. 이메일 초안을 만들고 발송 전 승인 단계에서 멈춥니다.

## Next Build Tasks

- 보도자료 템플릿 만들기
- fact-check checklist 추가
- 배포 dry-run 포맷 정의
