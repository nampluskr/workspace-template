# 워크스페이스 템플릿 정비 세션 핸드오프

> 작성일: 2026-06-05
> 세션 목적: writing-style.md 개선 및 워크스페이스 템플릿 파일 정비
> 이전 핸드오프: 260605-201612_session-handoff.md

---

## 1. 세션 핵심 요약

- `_workspace/prompts/` 경로 잔재를 `_workspace/commands/` 로 수정 (260605-061546_session-handoff.md 내 5곳)
- `README.md`, `PROJECT.md` 에 writing-style.md 규칙 적용 (메타정보 블록, 목차, H2/H3 번호, 서술체)
- `TASKS.md` 의 Stage/Phase 항목에서 콜론 제거
- `PROJECT.md` 의 Stage/Phase 항목에서 콜론 제거 (사용자가 직접 수정, 확인)
- `_workspace/docs/workspace-guide.md` 에 `README.md`, `PROJECT.md` 도 writing-style.md 적용 대상임을 명시
- `_workspace/rules/writing-style.md` 에 문체 규칙 개선 및 불릿 분리 규칙 추가
- `_workspace/rules/writing-style.md` 에서 코딩 스타일 관련 섹션을 분리하여 `coding-style.md` 신규 작성
- `sync-cli-guides` 명령어 추가 검토 → 보류 (CLAUDE.md / AGENTS.md 동기화 방식 미결)

---

## 2. 사용자 요청 및 의도

| 요청 내용 | 배경 목적 |
| --- | --- |
| `_workspace/prompts/` → `_workspace/commands/` 수정 | 이전 세션 잔재 정리 |
| `README.md`, `PROJECT.md` 에 writing-style.md 규칙 반영 | 워크스페이스 내 모든 문서의 일관성 확보 |
| `TASKS.md` 콜론 제거 | `PROJECT.md` 와 표기 방식 통일 |
| writing-style.md 에 기술/학술 문서 서술 방식 구분 반영 | AI CLI 가 문서 작성 시 서술 방식을 명확히 적용하도록 |
| 독립 항목이 하나의 문단에 있는 경우 불릿 분리 | 규칙 가독성 향상 및 AI CLI 의 정확한 해석을 위해 |
| 코딩 스타일을 별도 파일로 분리 | 문서 작성 규칙과 코딩 규칙의 관심사 분리 |

---

## 3. 확정된 결정사항

| 항목 | 확정 내용 | 비고 |
| --- | --- | --- |
| writing-style.md 적용 범위 | `README.md`, `PROJECT.md` 포함 | workspace-guide.md 섹션 6에 명시 |
| 문체 규칙 | "상세한 기술 문서 또는 전문적인 학술 문서 형식으로 작성한다" 단일 기준으로 통일 | 기술/학술 자동 구분 방식 불채택 |
| 불릿 분리 기준 | 서로 독립적인 항목이 하나의 문단에 있을 때 분리, 하나의 개념을 연속 서술하는 경우 유지 | writing-style.md 섹션 2.6으로 추가 |
| 코딩 스타일 분리 | `_workspace/rules/coding-style.md` 신규 작성 | 섹션 3 파일/폴더 규칙, 섹션 11 Jupyter Book 규칙은 writing-style.md 유지 |
| writing-style.md 섹션 구성 | 10개 섹션으로 재정렬 (구 7 코드 블록, 구 10 Jupyter Notebook 제거) | |
| Stage/Phase 표기 | 콜론 없는 형식 (`Stage 1 {Stage명}`) | TASKS.md, PROJECT.md 동일 적용 |
| sync-cli-guides 명령어 | 보류 | CLAUDE.md / AGENTS.md 동기화 방식 별도 논의 필요 |

---

## 4. AI 핵심 제안 및 분석

- **불릿 분리 대상 선별**
  - writing-style.md 전체를 스캔하여 독립 항목이 혼재된 4곳(2.3 요약, 2.4 목차, 4.3 문체, 8.2 삽입 형식) 선별
  - 나머지(1.1 목적, 2.5 참고문헌, 4.1 본문 언어, 11.4 remove-cell)는 하나의 개념 연속 서술로 판단하여 유지

- **sync-cli-guides 동기화 방식 분석**
  - mtime 비교 방식은 Ctrl+S 저장만으로 갱신되어 신뢰 불가
  - 내용 비교 + mtime 조합 방식 제안
  - 현재 AI CLI 판별 방식은 두 CLI 번갈아 사용 시 마지막 수정 CLI 판단 불가 문제 존재
  - 결론: 보류, 별도 이슈로 재검토

---

## 5. 미결 사항

| # | 항목 | 현재 상태 | 결정 필요 내용 |
| --- | --- | --- | --- |
| 1 | CLAUDE.md / AGENTS.md 동기화 | 보류 | sync-cli-guides 명령어 방식 (mtime, 내용 비교, 현재 CLI 판별 등) 확정 필요 |
| 2 | writing-style.md 수정일 갱신 | 미반영 | 이번 세션에서 수정된 내용 반영하여 수정일 갱신 필요 |
| 3 | coding-style.md 적용 범위 | 미명시 | workspace-guide.md 또는 CLAUDE.md 에 coding-style.md 참조 안내 추가 여부 |

---

## 6. 다음 작업 목록

| 우선순위 | 작업 | 관련 폴더/파일 | 사용할 도구 |
| --- | --- | --- | --- |
| 1 | writing-style.md, coding-style.md 수정일 갱신 | `_workspace/rules/` | Claude Code |
| 2 | CLAUDE.md / AGENTS.md 동기화 방식 재검토 및 sync-cli-guides 명령어 추가 | `_workspace/commands/` | Claude Code |
| 3 | coding-style.md 참조를 workspace-guide.md 또는 CLAUDE.md 에 추가 여부 결정 | `_workspace/docs/workspace-guide.md`, `CLAUDE.md` | Claude Code |

---

## 7. 다음 세션에서 이어받기

### 새 세션 시작 지시문:

"아래는 이전 세션의 컨텍스트입니다.
이 내용을 기반으로 워크스페이스 템플릿 정비를 이어서 진행해 주세요.

특히 다음 항목을 우선적으로 다뤄주세요:
1. `_workspace/rules/writing-style.md` 와 `_workspace/rules/coding-style.md` 의 수정일 갱신
2. `CLAUDE.md` / `AGENTS.md` 동기화 방식 재검토 (`_workspace/commands/sync-cli-guides.md` 명령어 추가)
3. `coding-style.md` 를 워크스페이스 운영 문서에 참조 추가 여부 결정"

---

## 8. 참고 자료 및 링크

| 항목 | 위치/경로 | 용도 |
| --- | --- | --- |
| 문서 작성 스타일 가이드 | `_workspace/rules/writing-style.md` | 문서 작성 공통 규칙 |
| 코딩 스타일 가이드 | `_workspace/rules/coding-style.md` | 코드 작성 공통 규칙 (이번 세션 신규) |
| 워크스페이스 가이드 | `_workspace/docs/workspace-guide.md` | 워크스페이스 사용법 |
| 이전 핸드오프 | `_workspace/sessions/260605-201612_session-handoff.md` | 이전 세션 컨텍스트 |
