# 문서 정비 및 메타정보 전환 세션 핸드오프

> 작성일: 2026-06-05
> 세션 목적: 문서 중복/충돌 해소, 메타정보 태그→주제 전환, project-init 명령어 개선
> 이전 핸드오프: `_workspace/sessions/260605-225230_session-handoff.md`

---

## 1. 세션 핵심 요약

- 루트 필수 파일과 `_workspace/` 문서 간 중복 내용 및 충돌 전수 점검
- Subject code 표를 `subject-classification.md` 단일 출처로 통합, 상위 문서는 참조만
- 커스텀 명령어 상세 설명을 `workspace-guide.md §5` 단일 출처로 통합
- CLAUDE.md / AGENTS.md 완전 동기화 (목차 형식, 호출 방식, 참조 링크)
- 메타정보 블록의 `태그` 항목을 subject 전체명 기반 `주제` 항목으로 전환 (9개 파일)
- `subject-classification.md` 파일명 유지 결정 (`subjects.md`, `subject-list.md` 검토 후)
- `project-init.md` 명령어 개선: 진행 단계 AI 초안 제시 방식, Task AI 자동 작성, 폴더 구조 확인/생성 절차 파일 작성 전 단계로 이동
- `README.md` 목차 번호 목록 형식으로 수정

---

## 2. 사용자 요청 및 의도

| 요청 내용 | 배경 목적 |
| --- | --- |
| 루트 파일과 `_workspace/` 내 문서 중복/충돌 확인 | 단일 출처 원칙 확립, 문서 유지보수 부담 감소 |
| 메타정보 `태그` → `주제` 전환 | subject 분류 체계와 메타정보 일관성 확보 |
| `project-init` 진행 단계 AI 초안 방식으로 변경 | 사용자가 직접 입력하는 부담 감소, AI와 대화형으로 구조 확정 |
| `project-init` 폴더 구조 확인/생성 절차 추가 | 파일 내에 폴더 구조가 포함되므로 파일 작성 전에 확정 필요 |
| CLAUDE.md vs AGENTS.md 동일 여부 확인 및 동기화 | AI CLI 공통 지침이므로 CLI 전용 분기 없이 동일 내용 유지 |

---

## 3. 확정된 결정사항

| 항목 | 확정 내용 |
| --- | --- |
| Subject code 표 단일 출처 | `subject-classification.md` 만 표 보유, 상위 문서는 참조 링크만 |
| 커스텀 명령어 상세 설명 단일 출처 | `workspace-guide.md §5`, CLAUDE.md/AGENTS.md 는 참조 링크만 |
| 메타정보 `태그` 폐기 | subject 전체명(영어)을 값으로 하는 `주제` 항목으로 전환 |
| `subject-classification.md` 파일명 | 현행 유지 (`subjects.md`, `subject-list.md` 검토 후) |
| CLAUDE.md / AGENTS.md | 완전 동일 유지, CLI 전용 분기 없음 |
| `project-init` 진행 단계 수집 방식 | AI가 목적/배경/범위 기반 Stage-Phase 초안 제시 → 사용자 피드백 반영 |
| `project-init` Task 작성 방식 | AI가 확정된 Stage-Phase 기반으로 직접 작성 |
| `project-init` 폴더 구조 단계 위치 | 확인 및 수정 완료 후, 파일 작성 전 단계로 확정 |

---

## 4. AI 핵심 제안 및 분석

- **상위 문서 참조 구조 제안**
  - 동일 내용이 여러 파일에 직접 기술되는 대신, 상위 문서가 하위 문서를 참조하는 방식
  - Subject code 표(4곳 중복) → `subject-classification.md` 단일 출처로 통합
  - 커스텀 명령어 목록(3곳 중복) → `workspace-guide.md §5` 단일 출처로 통합

- **`주제` 항목 값 형식**
  - `subject-classification.md` 의 Subject 열 전체명(예: `Mathematics`, `Machine Learning`) 사용
  - 복수 주제는 쉼표로 구분

---

## 5. 미결 사항

없음

---

## 6. 다음 작업 목록

| 우선순위 | 작업 | 관련 파일 |
| --- | --- | --- |
| 1 | `project-init 실행` 으로 실제 프로젝트 명세 작성 | `PROJECT.md`, `TASKS.md`, `README.md` |

---

## 7. 다음 세션에서 이어받기

### 새 세션 시작 지시문

"아래는 이전 세션의 컨텍스트입니다.
 이 내용을 기반으로 작업을 이어서 진행해 주세요.

 session-start 실행 후 project-init 실행 으로 실제 프로젝트 명세 작성을 진행해 주세요."

---

## 8. 참고 자료 및 링크

| 항목 | 위치/경로 |
| --- | --- |
| 커스텀 명령어 폴더 | `_workspace/commands/` |
| 워크스페이스 가이드 | `_workspace/docs/workspace-guide.md` |
| 변경 이력 | `_workspace/docs/workspace-history.md` |
| 주제 분류 체계 | `_workspace/rules/subject-classification.md` |
