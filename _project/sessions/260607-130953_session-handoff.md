# 워크스페이스 템플릿 세션 핸드오프

> 작성일시: 260607-130953
> 세션 목적: 프로젝트 관리 파일명 변경 및 워크스페이스 설정 보완
> 이전 핸드오프: 260607-125505_session-handoff.md

## 1. 세션 핵심 요약

- `_project/TASKS.md` 를 `_project/PROJECT-TODO.md` 로 파일명 변경 (HISTORY-TODO.md 를 거쳐 최종 확정)
- 파일명 변경에 따라 모든 운영 파일의 참조를 일괄 수정 (CLAUDE.md, AGENTS.md, PROJECT.md, PROJECT-HISTORY.md, commands/ 하위 5개 파일)
- 디렉토리 구조 코드 블록에 `PROJECT-HISTORY.md` 항목 추가
- `session-handoff` 실행 시 승인 없이 자동 진행되도록 `.claude/settings.local.json` 에 허용 규칙 추가

## 2. 사용자 요청 및 의도

| 요청 내용 | 배경 목적 |
| --- | --- |
| TASKS.md → HISTORY-TODO.md 로 변경 | 파일명에 역할을 더 명확히 표현 |
| HISTORY-TODO.md → PROJECT-TODO.md 로 재변경 | PROJECT- 접두사로 프로젝트 관리 파일군 일관성 확보 |
| 디렉토리 구조에 PROJECT-HISTORY.md 추가 | 구조 문서와 실제 파일 일치 |
| session-handoff 자동 승인 설정 | 세션 종료 절차의 마찰 제거 |

## 3. 확정된 결정사항

| 항목 | 확정 내용 | 비고 |
| --- | --- | --- |
| 작업 목록 파일명 | `_project/PROJECT-TODO.md` | 기존 TASKS.md 대체 |
| 디렉토리 구조 표기 | PROJECT-TODO.md, PROJECT-HISTORY.md 모두 명시 | CLAUDE.md, AGENTS.md 동기화 |
| session-handoff 허용 규칙 | `.claude/settings.local.json` 에 date, ls, Read, Write 허용 추가 | |

## 4. AI 핵심 제안 및 분석

- **세션 핸드오프 자동 승인 범위 설정**
  - `date *`, `ls _project/sessions*`, `Read(_project/PROJECT.md)`, `Read(_project/PROJECT-TODO.md)`, `Read/Write(_project/sessions/*)` 를 허용 목록에 추가
  - session-handoff 실행에 필요한 최소 권한만 부여하여 보안 원칙 유지

## 5. 미결 사항

없음.

## 6. 다음 작업 목록

| 우선순위 | 작업 | 관련 폴더/파일 | 사용할 도구 |
| --- | --- | --- | --- |
| 1 | project-init 실행으로 실제 프로젝트 초기화 | `_project/PROJECT-TODO.md`, `_project/PROJECT.md` | project-init 커스텀 명령어 |

## 7. 다음 세션에서 이어받기

### 새 세션 시작 지시문:

"session-start 실행 후 실제 프로젝트 작업을 시작해 주세요."

## 8. 참고 자료 및 링크

| 항목 | 위치/경로 | 용도 |
| --- | --- | --- |
| 작업 목록 | `_project/PROJECT-TODO.md` | Stage-Phase-Task 진행 관리 |
| 완료 이력 | `_project/PROJECT-HISTORY.md` | 완료 Task 상세 기록 |
| 허용 설정 | `.claude/settings.local.json` | Claude Code 자동 승인 규칙 |
