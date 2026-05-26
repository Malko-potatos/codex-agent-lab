# Codex Agent Lab

Codex를 기반으로 반복 문서 업무와 운영 업무를 자동화하기 위한 에이전트를 만드는 스터디 저장소입니다.

이 저장소는 개발자만을 위한 프레임워크 문서가 아닙니다. 비전공 대학생이나 직장인도 “내 반복 업무를 Codex에게 어떻게 맡길 수 있을까?”를 직접 실습해 보는 가이드 repo입니다.

이 저장소에서 가장 중요한 에이전트는 **0번 에이전트 하네스 번역기**입니다. 여기서 하네스는 “에이전트가 안전하게 일하도록 잡아주는 작업대”라고 생각하면 됩니다. 다른 에이전트를 만들 사람들은 본인이 원하는 작업을 먼저 0번 에이전트에 넣고, 그 작업을 Codex의 `AGENTS.md`, `.codex.toml`, skill, MCP, hook, subagent 설계로 번역합니다.

이 저장소는 public repository로 공개할 수 있는 골격만 담습니다. 실제 고객 문서, 급여/세금/계약 데이터, 네이버웍스 인증 정보, 기자 연락처, 크롤링 원문 데이터, 내부 업무 기록은 이 저장소에 커밋하지 않습니다.

## 목적

- 수강생이 반복 문서 업무와 운영 업무를 에이전트 아이디어로 바꿔 봅니다.
- 어려운 용어는 파인만 학습법처럼 쉬운 말과 예시로 풀어 설명합니다.
- 0번 하네스 번역기로 자연어 업무 아이디어를 Codex 에이전트 설계로 바꿉니다.
- 각 폴더를 하나의 Codex 기반 에이전트 후보로 관리합니다.
- 아이디어 단계, 프로토타입 단계, 운영 단계가 섞이지 않도록 상태를 명시합니다.
- 나중에 GitHub public repo로 올려도 민감정보가 노출되지 않는 구조를 유지합니다.

## 학습 대상

- 반복되는 문서 작업을 줄이고 싶은 직장인
- AI 에이전트를 업무에 어떻게 적용하는지 배우고 싶은 대학생
- 개발 지식은 많지 않지만 Codex로 업무 자동화를 실습하고 싶은 수강생
- 회사 자료를 안전하게 다루는 AI 업무 흐름을 배우고 싶은 운영 담당자

## 용어 설명 원칙

이 저장소는 어려운 기술 용어를 그대로 외우게 하지 않습니다.

예를 들어 에이전트는 “반복 업무를 맡기는 작은 업무 도우미”로, hook은 “위험한 행동 전에 멈추는 검문소”로 설명합니다.

자세한 용어 풀이는 `docs/plain-language-glossary.md`에서 확인합니다.

## 설계 범위 원칙

이 저장소의 에이전트는 Codex가 이미 제공하는 하네스 부품을 조립해 만드는 것을 원칙으로 합니다.

1. **Codex 런타임 수정이 필요한 경우는 제외합니다.** Codex 자체의 실행 엔진, 샌드박스, 권한 시스템, 내부 런타임을 바꿔야만 가능한 아이디어는 이 저장소의 대상이 아닙니다.
2. **서브에이전트는 허용하지만, 멀티에이전트 오케스트레이션이 필요한 경우는 제외합니다.** 병렬 조사, 파일 분석, 검토처럼 부모 에이전트가 명확히 위임하고 회수할 수 있는 subagent는 사용할 수 있습니다. 별도 orchestrator, 장기 상태 공유, agent 간 자율 협상, 복잡한 라우팅이 필요한 구조는 다루지 않습니다.
3. **로컬 에이전트를 지향합니다.** 기본 산출물은 로컬 Codex 환경에서 동작하는 `AGENTS.md`, `.codex.toml`, skill, hook, MCP 명세입니다. Cloud, 외부 서버, 상시 실행 백엔드는 꼭 필요한 경우에만 별도 검토합니다.

## 하네스 번역 흐름

```text
원하는 작업 아이디어
  -> 00-agent-harness-translator
  -> 부품별 명세 표
  -> AGENTS.md / .codex.toml / skill / MCP / hook / subagent 초안
  -> 개별 에이전트 폴더 구현
```

0번 에이전트가 번역하는 부품은 네 축으로 나뉩니다.

- 지시: 시스템 프롬프트, 입력 프롬프트
- 지식/상태: 메모리, skill
- 능력/행동: MCP, 서브에이전트
- 제어/횡단: hook

핵심 원칙은 간단합니다. **불변식과 실패 모드가 비어 있으면 아직 설계가 끝나지 않은 것입니다.**

메모리는 별도 주의가 필요합니다. Codex 공식 메모리는 repo 안 `MEMORY.md`가 아니라 사용자의 Codex home, 기본적으로 `~/.codex/memories/` 아래 생성되는 local recall layer입니다. 반드시 적용되어야 하는 팀 규칙은 memory가 아니라 `AGENTS.md`나 체크인된 문서에 둡니다. 이 저장소의 기준은 `docs/codex-memory-policy.md`를 따릅니다.

## 폴더 구조

```text
.
|-- AGENTS.md
|-- .codex.toml
|-- .env.example
|-- .gitignore
|-- docs/
|   |-- codex-memory-policy.md
|   |-- idea-review-checklist.md
|   |-- plain-language-glossary.md
|   |-- security-and-privacy.md
|   `-- week-1-agent-selection.md
`-- agents/
    |-- _template/
    |-- 00-agent-harness-translator/
    |-- 01-business-plan-hwp/
    |-- 02-result-report-draft/
    |-- 03-naver-works-photo-finder/
    |-- 04-quote-derivative-estimator/
    |-- 05-proposal-draft-from-rfp/
    |-- 06-satisfaction-survey-form/
    |-- 07-instructor-cafe-user-research/
    |-- 08-naver-works-executive-assistant/
    |-- 09-document-automation-system/
    |-- 10-multi-agent-ai-employee-team/
    |-- 11-press-release-journalist-distribution/
    |-- 12-social-content-autopublisher/
    |-- 13-public-grant-document-review/
    |-- 14-event-website-builder/
    |-- 15-keyword-clipping-newsletter/
    `-- 16-employee-workflow-memory/
```

각 에이전트 폴더는 최소한 아래 두 파일을 가집니다.

- `AGENTS.md`: Codex가 해당 에이전트 폴더에서 따라야 할 작업 지침
- `.codex.toml`: 에이전트 목적, 입력, 출력, 도구, 승인 정책의 메타 설정

## 에이전트 목록

| No. | 폴더 | 아이디어 |
| --- | --- | --- |
| 00 | `agents/00-agent-harness-translator` | 작업 아이디어를 Codex 하네스 부품 명세로 번역 |
| 01 | `agents/01-business-plan-hwp` | 사업 계획서 `.hwp` 작성 에이전트 |
| 02 | `agents/02-result-report-draft` | 결과보고서 초안 작성 |
| 03 | `agents/03-naver-works-photo-finder` | 네이버웍스 연동 사진 찾기 |
| 04 | `agents/04-quote-derivative-estimator` | 견적서 데이터를 기반으로 타 견적서 만들기 |
| 05 | `agents/05-proposal-draft-from-rfp` | 제안요청서/과업지시서와 기존 제안서 기반 제안서 초안 |
| 06 | `agents/06-satisfaction-survey-form` | 만족도조사 설문폼 생성 |
| 07 | `agents/07-instructor-cafe-user-research` | 강사모 네이버카페 크롤링 기반 유저 리서치 |
| 08 | `agents/08-naver-works-executive-assistant` | 네이버웍스 기반 대표 AI 비서 |
| 09 | `agents/09-document-automation-system` | 반복 문서 자동생성 시스템 |
| 10 | `agents/10-multi-agent-ai-employee-team` | 멀티에이전트 AI 직원 팀 |
| 11 | `agents/11-press-release-journalist-distribution` | 보도자료 자동작성 및 기자 배포 |
| 12 | `agents/12-social-content-autopublisher` | 블로그/인스타 콘텐츠 자동생성 및 업로드 |
| 13 | `agents/13-public-grant-document-review` | 공공 지원사업 서류검토 운영 지원 |
| 14 | `agents/14-event-website-builder` | 행사 홈페이지 제작 |
| 15 | `agents/15-keyword-clipping-newsletter` | 키워드 클리핑 및 뉴스레터 |
| 16 | `agents/16-employee-workflow-memory` | 직원 업무 플로우 저장 |

## 운영 원칙

1. 모든 에이전트는 0번 하네스 번역기를 거쳐 부품별 명세를 먼저 작성합니다.
2. 모든 에이전트는 기본적으로 `draft-first`, `human-review-required` 방식으로 설계합니다.
3. 외부 전송, 업로드, 메시지 발송, 크롤링, 로그인 세션 사용은 명시 승인 후 실행합니다.
4. 공개 저장소에는 샘플 데이터만 둡니다.
5. 실제 자동화 구현 전에는 `docs/idea-review-checklist.md`로 사업성, 법적 리스크, 데이터 리스크를 검토합니다.
6. 에이전트가 만든 산출물은 초안이며 최종 제출물은 사람이 검토합니다.

## 다음 단계

1. 우선순위가 높은 에이전트 2-3개를 고릅니다.
2. 각 아이디어를 `agents/00-agent-harness-translator/templates/harness-parts-spec.md`로 번역합니다.
3. 메모리 후보를 공식 Codex memory, `AGENTS.md`, checked-in docs, skill 중 어디에 둘지 분리합니다.
4. 번역 결과로 개별 에이전트의 `AGENTS.md`, `.codex.toml`, memory contract, skill, MCP, hook 초안을 만듭니다.
5. 샘플 입력과 기대 출력 예시를 추가합니다.
6. 필요한 외부 서비스와 승인 흐름을 정합니다.
7. 실제 자동화 스크립트, 템플릿, 테스트를 추가합니다.
