# 에이전트 산출물 생성 체크리스트

이 문서는 0번 에이전트 하네스 번역기가 새 에이전트 폴더를 만들거나 기존 에이전트 폴더를 고칠 때 사용하는 검수표입니다.

## 공통 전제

- 공개 저장소에 실제 고객 문서, 원문 데이터, 인증정보, 개인정보를 넣지 않습니다.
- 모든 외부 전송, 업로드, 게시, 발송, 로그인 세션 사용은 기본값을 `dry-run`으로 둡니다.
- 산출물은 초안이며 최종 제출과 실행은 사람이 검토합니다.
- 실패 모드와 불변식이 비어 있으면 설계가 끝난 것으로 보지 않습니다.

## `AGENTS.md` 생성 체크리스트

### 1. Mission

- 에이전트가 맡는 일을 한 문장으로 썼는지 확인합니다.
- 맡지 않는 일과 위험한 자동화를 명시했는지 확인합니다.
- 최종 산출물이 아니라 초기 검증 산출물의 형식을 분리했는지 확인합니다.

### 2. Status

- `Stage`가 `idea`, `prototype`, `operational`, `core` 중 하나인지 확인합니다.
- `Output mode`가 실제 사용 방식과 맞는지 확인합니다.
- `Human review`가 필요한 위치를 숨기지 않았는지 확인합니다.

### 3. Inputs

- `Required`, `Optional`, `Sensitive`를 분리했는지 확인합니다.
- 필수 입력이 없을 때 질문으로 멈추는 규칙이 있는지 확인합니다.
- 민감 입력은 public repo에 저장하지 않는다고 적었는지 확인합니다.

### 4. Outputs

- 사용자가 바로 검토할 수 있는 산출물 이름으로 적었는지 확인합니다.
- 누락 정보, 검토표, 승인 대기 항목 같은 안전 산출물을 포함했는지 확인합니다.
- 외부 발송/게시 결과를 산출물로 오해하게 만들지 않았는지 확인합니다.

### 5. Operating Rules

- 숫자, 금액, 일정, 법적 판단, 공식 제출 내용은 근거 없는 추정을 금지했는지 확인합니다.
- 외부 API, 브라우저, 메일, 게시 도구 사용 전 승인 지점을 적었는지 확인합니다.
- 샘플/더미 데이터와 실제 운영 데이터를 분리했는지 확인합니다.
- 반드시 적용되어야 하는 규칙과 memory 후보를 분리했는지 확인합니다.

### 6. Suggested Workflow

- 첫 단계가 입력 확인 또는 범위 확인인지 확인합니다.
- 초안 생성 전에 구조화/대응표/검증표를 만드는지 확인합니다.
- 마지막 단계가 사람 검토 또는 승인 대기인지 확인합니다.

### 7. Next Build Tasks

- 다음 작업이 2-4개 정도의 작은 단위인지 확인합니다.
- 첫 작업은 public-safe 샘플이나 템플릿으로 검증 가능한지 확인합니다.
- 외부 연동 작업은 정책 검토와 dry-run 뒤에 배치했는지 확인합니다.

### 8. Memory Contract

- 공식 Codex memory가 repo 안 `MEMORY.md`가 아니라 `~/.codex/memories/` 아래 생성 상태임을 전제했는지 확인합니다.
- 항상 적용되어야 하는 규칙을 `AGENTS.md`나 checked-in docs에 두었는지 확인합니다.
- memory 후보가 stable preference, recurring workflow, convention, known pitfall, 진행 상태 중 무엇인지 분류했는지 확인합니다.
- 저장 금지 데이터에 secrets, credentials, private originals, personal data가 포함되어 있는지 확인합니다.
- 저장 시점이 즉시가 아니라 eligible thread가 idle 상태가 된 뒤 background로 생성될 수 있음을 적었는지 확인합니다.
- 사용자가 `/memories` 또는 Codex 앱 설정으로 thread-level control을 할 수 있음을 적었는지 확인합니다.
- 공유 전 `~/.codex/memories/` 검토와 부적절한 기억 삭제/수정 절차를 적었는지 확인합니다.

## `.codex.toml` 생성 체크리스트

### 1. `[agent]`

- `id`가 폴더명과 일치하는지 확인합니다.
- `status`가 `AGENTS.md`의 Stage와 일치하는지 확인합니다.
- `visibility = "public-skeleton-only"`를 유지하는지 확인합니다.

### 2. `[scope]`

- `goal`이 실행 가능한 한 문장인지 확인합니다.
- `target_users`가 실제 검토자나 사용자와 맞는지 확인합니다.
- `non_goals`에 위험한 자동화와 과장된 범위를 넣었는지 확인합니다.

### 3. `[inputs]`

- `required`만으로 최소 동작이 가능한지 확인합니다.
- `optional`이 있으면 없을 때도 동작 방식이 있는지 확인합니다.
- `sensitive`에 인증, 개인정보, 내부 문서, 고객 정보가 빠지지 않았는지 확인합니다.

### 4. `[outputs]`

- `primary`가 초안, 검토표, 체크리스트 중심인지 확인합니다.
- `formats`가 현재 구현 단계와 맞는지 확인합니다.
- 미래 형식은 `hwp-future`, `pdf-future`처럼 구분했는지 확인합니다.

### 5. `[tools]`

- `required`는 로컬에서 검증 가능한 능력 위주인지 확인합니다.
- 외부 서비스는 `external_services`에 명시했는지 확인합니다.
- 아직 구현하지 않은 API는 `optional` 또는 `future` 성격으로 두었는지 확인합니다.

### 6. `[safety]`

- `human_review_required = true`인지 확인합니다.
- `external_actions_default = "dry_run"`인지 확인합니다.
- `approval_required_for`가 실제 위험 행동을 포함하는지 확인합니다.
- `data_policy`가 커밋 금지 대상을 직접 말하는지 확인합니다.

### 7. `[workflow]`

- 단계가 입력 확인에서 검토 산출물까지 이어지는지 확인합니다.
- `validation`에 테스트 가능한 규칙이 들어 있는지 확인합니다.
- 불변식 위반 시 멈추거나 질문하는 경로가 있는지 확인합니다.

### 8. `[memory_contract]`

- `official_storage`가 `~/.codex/memories/`를 가리키는지 확인합니다.
- `repo_policy`가 실제 generated memories를 repo에 저장하지 않는다고 말하는지 확인합니다.
- `source_of_truth`가 `AGENTS.md`/docs와 Codex memories의 경계를 분리하는지 확인합니다.
- `must_define`에 기억 목적, 저장 금지, 저장 위치, 저장/사용 시점, thread control, 검토/삭제가 포함되는지 확인합니다.

## 완료 판정

새 에이전트 폴더는 아래 조건을 모두 만족해야 초안 완료로 봅니다.

- `AGENTS.md`와 `.codex.toml`이 서로 같은 mission, status, safety 정책을 말합니다.
- memory contract가 공식 Codex memory 동작과 source-of-truth 경계를 반영합니다.
- 하네스 부품 명세에서 시스템 프롬프트, 입력 프롬프트, 메모리, skill, MCP, subagent, hook의 입력/출력/실패 모드/불변식이 모두 채워져 있습니다.
- public repo safety 검토가 끝났고 실제 데이터가 없습니다.
- 다음 구현 작업이 샘플 데이터 또는 dry-run으로 시작합니다.
