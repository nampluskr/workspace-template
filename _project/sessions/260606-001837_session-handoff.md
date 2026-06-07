# project-update 명령어 추가 및 문서 문체 통일 세션 핸드오프

> 작성일시: 260606-001837
> 세션 목적: project-update 명령어 신규 추가, 명령어 문서 문체 통일, 문서 작성 규칙 이동
> 이전 핸드오프: `_workspace/sessions/260605-225230_session-handoff.md`

---

## 1. 세션 핵심 요약

- `project-update` 명령어 신규 추가 — 자유 형식 입력으로 PROJECT.md / TASKS.md / README.md 선택적 갱신
- `_workspace/commands/` 내 전체 명령어 파일 문체 통일 (`~합니다` → `~한다`, `~입니다` → `~이다`)
- 문서 작성 규칙(문체 3개 항목)을 `CLAUDE.md` / `AGENTS.md` §9 로 이동
- `writing-style.md` §4.3 에 `CLAUDE.md` / `AGENTS.md §9` 를 원본으로 참조하는 문구 추가
- `workspace-guide.md` §5 커스텀 명령어 테이블에 `project-update` 행 추가
- `CLAUDE.md` / `AGENTS.md` 목차 §9 문서 작성 규칙 추가, 기존 §9→§10 번호 변경

---

## 2. 사용자 요청 및 의도

| 요청 내용 | 배경 목적 |
| --- | --- |
| project-update 명령어 추가 | project-init 은 시작 시 순서대로 수집하는 구조라 진행 중 단편적 수정에 부적합 |
| 명령어 문서 전체 문체 수정 | writing-style.md 규칙(`~한다`, `~이다`)과 실제 문서가 불일치 |
| 문체 규칙을 CLAUDE.md / AGENTS.md 로 이동 | AI CLI 가 가장 먼저 읽는 최상위 지침 파일에 문체 규칙이 있어야 일관 적용 가능 |

---

## 3. 확정된 결정사항

| 항목 | 확정 내용 |
| --- | --- |
| 신규 명령어명 | `project-update` (`project-edit`, `project-patch` 검토 후 확정) |
| project-update 동작 | 자유 형식 입력 → 의도 파악 → 단순 추가 즉시 반영, 삭제·구조 변경은 확인 후 반영 |
| 코드 블록 내 안내 문구 | 사용자에게 출력되는 대화용 텍스트이므로 경어체(`~해 주세요`) 유지 |
| 문체 규칙 위치 | `CLAUDE.md` / `AGENTS.md §9` 가 원본, `writing-style.md §4.3` 은 참조 |

---

## 4. AI 핵심 제안 및 분석

- **`project-update` 명명 근거**
  - `project-init` 과 `init → update` 자연스러운 쌍을 이룸
  - `project-edit`: 단일 항목 수정 뉘앙스로 다중 수정에 부적합
  - `project-patch`: 개발자 용어로 일반 사용자에게 생소

- **코드 블록 내 경어체 유지 판단**
  - `writing-style.md §4.3` 은 본문(마크다운 문서 서술)에 적용되는 규칙
  - 코드 블록 안은 AI CLI 가 사용자에게 직접 출력하는 대화 텍스트이므로 경어체가 적절

---

## 5. 미결 사항

없음

---

## 6. 다음 작업 목록

| 우선순위 | 작업 | 관련 파일 |
| --- | --- | --- |
| 1 | `project-init 실행` 으로 실제 프로젝트 명세 작성 | `PROJECT.md`, `TASKS.md`, `README.md` |
| 2 | `project-update 실행` 동작 확인 (단순 추가 / 구조 변경 두 경우 모두 테스트) | `_workspace/commands/project-update.md` |

---

## 7. 다음 세션에서 이어받기

### 새 세션 시작 지시문

"아래는 이전 세션의 컨텍스트입니다.
 이 내용을 기반으로 작업을 이어서 진행해 주세요.

 session-start 실행 후 project-init 실행 으로 실제 프로젝트 명세 작성을 시작해 주세요."

---

## 8. 참고 자료 및 링크

| 항목 | 위치/경로 |
| --- | --- |
| 신규 명령어 | `_workspace/commands/project-update.md` |
| 커스텀 명령어 폴더 | `_workspace/commands/` |
| 워크스페이스 가이드 | `_workspace/docs/workspace-guide.md` |
| 변경 이력 | `_workspace/docs/workspace-history.md` |
