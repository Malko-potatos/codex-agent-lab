# Codex Memory Policy

이 저장소는 일상 업무에 Codex를 쓰려는 사용자를 위한 public-safe 에이전트 랩입니다. 따라서 메모리는 개발자가 임의로 repo 안에 `MEMORY.md`를 만들고 관리하는 방식이 아니라, Codex 공식 동작을 기준으로 설명하고 설계합니다.

## 공식 문서 기준

OpenAI Codex 문서 기준으로 메모리는 기본적으로 꺼져 있으며, Codex 앱 설정 또는 `~/.codex/config.toml`의 `[features] memories = true`로 켭니다. 메모리는 이전 thread의 유용한 맥락을 이후 작업에 가져오기 위한 기능이며, 안정적인 선호, 반복 워크플로우, 기술 스택, 프로젝트 관례, 알려진 실수 같은 내용을 기억할 수 있습니다.

공식 문서는 반드시 지켜야 하는 팀 지침을 `AGENTS.md`나 체크인된 문서에 두라고 안내합니다. 메모리는 도움이 되는 local recall layer일 뿐, 항상 적용되어야 하는 규칙의 유일한 근거가 아닙니다.

메모리 파일은 Codex home 아래에 저장됩니다. 기본 위치는 `~/.codex/memories/`이며, 요약, durable entries, recent inputs, prior thread evidence 같은 생성 상태를 포함합니다. 이 파일은 점검할 수 있지만 primary control surface로 직접 편집하는 것을 전제로 삼지 않습니다.

공식 문서:

- [Memories - Codex](https://developers.openai.com/codex/memories)
- [Chronicle - Codex](https://developers.openai.com/codex/memories/chronicle)
- [Custom instructions with AGENTS.md](https://developers.openai.com/codex/guides/agents-md)
- [Agent Skills - Codex](https://developers.openai.com/codex/skills)

## 이 저장소의 메모리 원칙

1. **Repo에는 메모리 정책과 샘플 schema만 둡니다.** 실제 개인 업무 맥락, 고객 문서, 인증정보, 내부 대화, 원문 데이터는 저장하지 않습니다.
2. **항상 적용되어야 하는 규칙은 `AGENTS.md`와 체크인된 docs에 둡니다.** 예: 보안 정책, 승인 필요 행동, public repo safety.
3. **Codex memories는 사용자의 로컬 Codex home에 생성되는 보조 기억으로 설명합니다.** 이 저장소는 `~/.codex/memories/` 내부 파일 구조에 의존하지 않습니다.
4. **업무 에이전트는 메모리 후보를 제안할 수 있지만, 실제 저장 여부는 Codex 설정과 thread-level memory control에 따릅니다.**
5. **외부 context를 많이 쓴 thread는 메모리 생성 제외를 검토합니다.** MCP, web search, tool search 등 외부 자료가 섞이면 `memories.disable_on_external_context` 같은 설정이 필요할 수 있습니다.
6. **Chronicle은 선택 기능으로만 설명합니다.** 화면 맥락을 통해 memory를 보강하지만, screen capture와 민감정보 리스크가 있으므로 일상 업무 사용자는 민감 화면, 회의, 커뮤니케이션 중에는 pause/disable을 우선 고려합니다.

## 메모리에 넣기 좋은 것

- 사용자가 반복해서 요청하는 산출물 형식
- 반복 업무의 public-safe 단계 요약
- 에이전트별 우선순위와 상태
- 자주 쓰는 더미 데이터 구조나 템플릿 선호
- 검토자가 항상 보는 체크포인트
- 이전 작업에서 확인된 비민감 실패 패턴

## 메모리에 넣으면 안 되는 것

- API key, 토큰, 쿠키, 비밀번호, 개인 계정 정보
- 고객 문서 원문, 제안서 원문, RFP 원문, 계약서, 급여/세금 자료
- 직원 개인정보, 고객 개인정보, 기자 연락처 목록
- 네이버웍스 메시지/파일 원문, 네이버카페 비공개 게시글
- 일시적 판단, 아직 검토되지 않은 추정, 오래된 마감/가격/법률 정보

## 하네스 번역기의 Memory Contract

각 에이전트 아이디어를 번역할 때 메모리 항목에는 아래를 반드시 적습니다.

| 항목 | 설명 |
|------|------|
| 기억 목적 | 다음 thread에서 무엇을 반복 설명하지 않기 위한 기억인가 |
| 기억 후보 | stable preference, recurring workflow, convention, known pitfall 중 무엇인가 |
| 저장 금지 | 이 업무에서 절대 memory에 들어가면 안 되는 데이터 |
| 저장 위치 | Codex 공식 memory는 `~/.codex/memories/`; repo에는 정책과 샘플만 저장 |
| 저장 시점 | thread가 충분히 끝나고 idle 상태가 된 뒤 생성될 수 있습니다. 즉시 저장된다고 가정하지 않습니다. |
| 사용 시점 | `memories.use_memories`가 켜져 있고 관련성이 높을 때 future session에 주입될 수 있음 |
| source of truth | 항상 적용될 규칙은 `AGENTS.md`/docs, 기억 보조는 Codex memories |
| thread control | 사용자는 `/memories` 또는 Codex 앱 설정으로 thread별 사용/생성 여부를 조정 |
| 검토/삭제 | 공유 전 `~/.codex/memories/`를 검토하고, 부적절한 기억은 삭제 또는 수정 |
| 실패 모드 | 오래된 기억, 잘못된 관련성, 민감정보 포함, 외부 context 오염 |
| 불변식 | secrets/private originals/personal data는 memory에 저장하지 않음 |

## 사용자 안내 문구

업무 에이전트가 메모리 후보를 발견하면 아래처럼 말합니다.

```text
이 내용은 다음에도 반복될 가능성이 있어 Codex memory 후보입니다.
다만 반드시 적용되어야 하는 규칙이라면 AGENTS.md나 문서에 남겨야 합니다.
민감정보가 없다면 현재 thread를 memory 생성에 사용해도 됩니다.
```

민감정보가 섞였으면 아래처럼 말합니다.

```text
이번 thread에는 민감 자료가 포함되어 있어 memory 생성 후보로 쓰지 않는 편이 안전합니다.
필요한 규칙은 민감정보를 제거한 요약만 AGENTS.md나 docs에 남기겠습니다.
```
