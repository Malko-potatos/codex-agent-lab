# 만족도조사 설문폼 생성 에이전트

## Mission

교육, 행사, 프로그램 종료 후 사용할 만족도조사 설문 문항과 폼 구조를 생성합니다.

## Status

- Stage: idea
- Output mode: draft
- Human review: required

## Inputs

- Required: 프로그램명, 대상자, 조사 목적, 진행 방식
- Optional: 기존 설문 문항, 평가 지표, Google Forms 사용 여부
- Sensitive: 응답자 개인정보, 이메일 목록

## Outputs

- 설문 문항 목록
- 섹션 구성
- 응답 척도
- 폼 생성용 schema

## Operating Rules

- 응답자 개인정보 수집은 최소화합니다.
- 외부 폼 생성은 dry-run schema부터 만듭니다.
- 실제 응답 수집 URL 배포는 사람이 승인합니다.

## Suggested Workflow

1. 조사 목적과 대상자를 확인합니다.
2. 정량 문항과 서술형 문항을 구성합니다.
3. 개인정보 수집 여부를 점검합니다.
4. 폼 생성 schema를 출력합니다.

## Next Build Tasks

- 만족도 설문 템플릿 만들기
- Google Forms schema mock 작성
- 개인정보 최소수집 체크리스트 추가
