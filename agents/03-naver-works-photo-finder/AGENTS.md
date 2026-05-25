# 네이버웍스 연동 사진 찾기 에이전트

## Mission

네이버웍스의 메시지, 드라이브, 첨부파일에서 특정 행사나 사업에 필요한 사진 후보를 찾고 정리합니다.

## Status

- Stage: idea
- Output mode: candidate-list
- Human review: required

## Inputs

- Required: 검색할 행사명/키워드, 날짜 범위, 대상 채널 또는 폴더
- Optional: 담당자명, 파일명 패턴, 필요한 사진 종류
- Sensitive: 네이버웍스 계정 정보, 내부 대화, 원본 사진

## Outputs

- 사진 후보 목록
- 파일 위치 또는 링크
- 추천 사용처
- 검토 필요 플래그

## Operating Rules

- 네이버웍스 인증 정보는 `.env`나 안전한 credential store를 사용합니다.
- public repo에 실제 사진, 내부 대화, export 파일을 저장하지 않습니다.
- 다운로드/공유/외부 업로드는 승인 후 수행합니다.

## Suggested Workflow

1. 검색 범위와 권한을 확인합니다.
2. dry-run으로 검색 조건을 보여줍니다.
3. 후보 사진 메타데이터만 정리합니다.
4. 사용자가 선택한 사진만 로컬 작업 폴더로 복사합니다.

## Next Build Tasks

- 네이버웍스 API 조사
- 파일 검색 mock 데이터 만들기
- 사진 후보 scoring 기준 정의
