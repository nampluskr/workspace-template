# 커스텀 명령어 체계 정비 세션 핸드오프

> 작성일시: 260605-225433
> 세션 목적: 커스텀 명령어 호출 방식 변경 및 session-start/end/project-init 명령어 추가
> 이전 핸드오프: `_workspace/sessions/260605-215637_session-handoff.md`

---

## 1. 세션 핵심 요약

- 커스텀 명령어 호출 방식을 `/{파일명}` 에서 `{파일명} 실행` / `@{파일명.md} 실행` 으로 변경
- `session-start.md`, `session-end.md`, `project-init.md` 3개 명령어 신규 추가
- `commit-message`, `session-handoff` 파일명 현행 유지 결정 (변경 검토 후)
- `session-start/end` 네이밍 확정 (`session-init/close` 대안 검토 후)
- `README.md` 를 연구/학습 워크스페이스 기준으로 재작성
- `workspace-guide.md` 섹션 5에 커스텀 명령어 테이블 추가
- `workspace-history.md` 에 5차 세션 내역 추가

---

## 2. 사용자 요청 및 의도

| 요청 내용 | 배경 목적 |
| --- | --- |
| 커스텀 명령어 호출 방식 변경 | `/project-init` 이 Claude Code 내장 명령어와 충돌하여 동작하지 않음 |
| session-start/end 명령어 추가 | 세션 시작/종료 시 반복 수행할 절차를 명령어로 표준화 |
| project-init 명령어 추가 | PROJECT.md 작성을 AI CLI 와 대화형으로 수행하고 싶음 |
| workspace-guide.md 커스텀 명령어 섹션 업데이트 | 신규 명령어를 가이드에 반영하여 문서와 실제 상태 동기화 |

---

## 3. 확정된 결정사항

| 항목 | 확정 내용 |
| --- | --- |
| 커스텀 명령어 호출 방식 | `{파일명} 실행` 또는 `@{파일명.md} 실행` 2가지 |
| 명령어 파일명 | `commit-message`, `session-handoff`, `session-start`, `session-end`, `project-init` |
| session-end 수행 순서 | TASKS.md 업데이트 → workspace-history.md 갱신 → session-handoff 실행 |
| project-init 출력 순서 | PROJECT.md → TASKS.md → README.md |
| README.md 구성 | 개요, 주제 분류, 디렉토리 구조 3개 섹션 |

---

## 4. AI 핵심 제안 및 분석

- **커스텀 명령어 호출 방식 2가지 병행**
  - `{파일명} 실행`: 간결한 텍스트 호출
  - `@{파일명.md} 실행`: IDE에서 파일 참조와 함께 호출 가능
  - 두 방식 모두 CLAUDE.md 및 각 명령어 파일에 명시

- **session-start/end 네이밍 채택 근거**
  - `session-init/close` 대안 검토: `init` 이 `project-init` 과 중복되어 혼동 가능
  - `start/end` 쌍이 대칭성과 반복 호출 적합성에서 우위

---

## 5. 미결 사항

없음

---

## 6. 다음 작업 목록

| 우선순위 | 작업 | 관련 파일 |
| --- | --- | --- |
| 1 | `project-init 실행` 으로 실제 프로젝트 명세 작성 테스트 | `PROJECT.md`, `TASKS.md` |
| 2 | `session-start 실행` 동작 확인 | `_workspace/commands/session-start.md` |

---

## 7. 다음 세션에서 이어받기

### 새 세션 시작 지시문

"아래는 이전 세션의 컨텍스트입니다.
 이 내용을 기반으로 작업을 이어서 진행해 주세요.

 session-start 실행 후 project-init 실행 으로 실제 프로젝트 명세 작성을 테스트해 주세요."

---

## 8. 참고 자료 및 링크

| 항목 | 위치/경로 |
| --- | --- |
| 커스텀 명령어 폴더 | `_workspace/commands/` |
| 워크스페이스 가이드 | `_workspace/docs/workspace-guide.md` |
| 변경 이력 | `_workspace/docs/workspace-history.md` |
