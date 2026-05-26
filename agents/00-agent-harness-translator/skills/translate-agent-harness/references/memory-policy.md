# 하네스 번역용 Memory 정책

이 문서는 0번 에이전트 하네스 번역 skill 안에서만 사용하는 memory 기준입니다. 0번 에이전트는 상위 폴더의 memory 문서를 참조하지 않고, 이 파일을 기준으로 memory contract를 작성합니다.

쉽게 말하면 memory는 “다음에도 같은 설명을 반복하지 않기 위해 남겨 두는 안전한 기억”입니다. 다만 고객 자료, 비밀번호, 계약서 원문처럼 민감한 내용은 기억하면 안 됩니다.

## 기본 원칙

1. 항상 적용되어야 하는 규칙은 memory가 아니라 `AGENTS.md`나 checked-in reference에 둡니다.
2. memory는 local recall layer입니다. 팀 규칙의 유일한 근거로 쓰지 않습니다.
3. 공식 Codex memory 위치는 `~/.codex/memories/`입니다.
4. 이 repo와 0번 skill 안에는 memory 정책과 public-safe 예시만 둡니다.
5. 실제 고객 문서, 개인정보, 인증정보, 내부 원문 데이터는 memory 후보로도 쓰지 않습니다.

## memory에 넣기 좋은 것

- 사용자가 반복해서 선호하는 산출물 형식
- public-safe 업무 단계 요약
- 에이전트별 우선순위와 상태
- 반복되는 검토 체크포인트
- 민감정보가 제거된 실패 패턴

## memory에 넣으면 안 되는 것

- API key, 토큰, 쿠키, 비밀번호
- 고객 문서 원문, 제안서 원문, RFP 원문, 계약서, 급여/세금 자료
- 직원 개인정보, 고객 개인정보, 기자 연락처 목록
- 네이버웍스 메시지/파일 원문, 비공개 커뮤니티 글
- 아직 검토되지 않은 추정, 오래된 마감/가격/법률 정보

## Memory Contract 필수 항목

| 항목 | 설명 |
|------|------|
| 기억 목적 | 다음 thread에서 무엇을 반복 설명하지 않기 위한 기억인지 적습니다. |
| 기억 후보 | stable preference, recurring workflow, convention, known pitfall, 진행 상태 중 무엇인지 적습니다. |
| 저장 금지 | 이 업무에서 절대 memory에 들어가면 안 되는 데이터를 적습니다. |
| 저장 위치 | 공식 Codex memory는 `~/.codex/memories/`; repo에는 정책과 샘플만 둡니다. |
| 저장 시점 | thread가 충분히 끝나고 idle 상태가 된 뒤 생성될 수 있습니다. 즉시 저장된다고 가정하지 않습니다. |
| 사용 시점 | memory 사용이 켜져 있고 관련성이 높을 때 다음 session에 주입될 수 있습니다. |
| source of truth | 항상 적용될 규칙은 `AGENTS.md`나 skill reference에 두고, memory는 보조 기억으로 둡니다. |
| 검토/삭제 | 공유 전 memory 내용을 검토하고, 부적절한 기억은 삭제 또는 수정합니다. |
| 실패 모드 | 오래된 기억, 잘못된 관련성, 민감정보 포함, 외부 context 오염을 적습니다. |
| 불변식 | secrets, private originals, personal data는 memory에 저장하지 않습니다. |

## 사용자 안내 문구

```text
이 내용은 다음에도 반복될 가능성이 있어 memory 후보입니다.
다만 반드시 지켜야 하는 규칙이라면 AGENTS.md나 skill reference에 남겨야 합니다.
민감정보가 없다면 memory 후보로 둘 수 있습니다.
```

민감정보가 섞였으면 아래처럼 말합니다.

```text
이번 설명에는 민감 자료가 포함될 수 있어 memory 후보로 쓰지 않는 편이 안전합니다.
필요한 규칙은 민감정보를 제거한 요약만 AGENTS.md나 skill reference에 남기겠습니다.
```
