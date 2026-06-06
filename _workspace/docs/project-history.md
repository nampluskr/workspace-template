# 프로젝트 작업 이력

이 문서는 프로젝트의 세션별 작업 내역과 주요 결정사항을 시간 순서로 기록한다.
각 항목은 세션 핸드오프 문서를 기반으로 작성하며, 향후 작업 맥락 파악과 의사결정 근거 추적에 활용한다.

> 생성일시: 260605-220755
> 수정일시: 260606-074638
> 주제: Development Environment and Tools

**목차**

1. [변경 이력 요약](#1-변경-이력-요약)
2. [세션별 상세 내역](#2-세션별-상세-내역)

## 1. 변경 이력 요약

| 날짜 | 시각 | 세션 | 주요 변경 내용 |
| --- | --- | --- | --- |
| 260605 | 195326 | 1차 | 워크스페이스 템플릿 최초 설계 및 필수 파일 생성 |
| 260605 | 202038 | 2차 | 워크스페이스 가이드 문서 신규 작성 및 AI CLI 지침 파일 정비 |
| 260605 | 220755 | 3차 | writing-style.md 개선 및 coding-style.md 분리 |
| 260605 | 220755 | 4차 | 주제 분류 체계(subject-classification.md) 도입 |
| 260605 | 225433 | 5차 | 커스텀 명령어 체계 정비 및 session-start/end/project-init 명령어 추가 |
| 260605 | 233851 | 6차 | 문서 중복/충돌 해소, 메타정보 태그→주제 전환, project-init 명령어 개선 |
| 260606 | 001837 | 7차 | project-update 명령어 추가, 전체 명령어 문서 문체 통일, 문서 작성 규칙 CLAUDE.md/AGENTS.md 이동 |
| 260606 | 072548 | 8차 | 섹션 번호 형식 변경(점 추가), 세션 핸드오프 파일명 오류 수정, session-end/handoff 파일명 지침 추가 |
| 260606 | 075523 | 9차 | 메타정보 형식 변경(생성일시/수정일시, YYMMDD-HHMMSS), workspace-guide §5 SSOT 미채택 이유 추가, project-history §1 시각 컬럼 추가 |
| 260607 | 074159 | 10차 | CLAUDE.md 섹션 재구성(§2 문서 작성 규칙 앞으로, §3 AI CLI 응답 스타일 신설), 개조식 원칙 전면 적용, README.md 프로젝트 템플릿으로 교체, workspace-readme.md 신규 생성, AGENTS.md 동기화 |

## 2. 세션별 상세 내역

### 2.1. 1차 세션 — 워크스페이스 템플릿 최초 설계

> 참조: `_workspace/sessions/260605-061546_session-handoff.md`

**배경**

GitHub 연계 로컬 워크스페이스에서 Claude Code, Codex, RooCode 같은 AI CLI를 활용한 프로젝트 수행을 위한 공통 템플릿이 필요했다. 딥러닝/ML 특화 구조에서 출발했으나 범용 구조로 확장하였다.

**신규 생성 파일 및 폴더**

| 파일/폴더 | 내용 |
| --- | --- |
| `README.md` | 외부 공개용 프로젝트 소개 템플릿 |
| `PROJECT.md` | 내부 프로젝트 명세 템플릿 |
| `TASKS.md` | Stage - Phase - Task 단위 진행 관리 템플릿 |
| `CLAUDE.md` | AI CLI 운영 지침 (다른 CLI 사용 시 복사 후 rename) |
| `_workspace/commands/session-handoff.md` | `/session-handoff` 커스텀 명령어 정의 |
| `_workspace/commands/commit-message.md` | `/commit-message` 커스텀 명령어 정의 |

**주요 결정사항**

| 항목 | 결정 내용 |
| --- | --- |
| 초기화 방식 | `workspace-template/` 폴더 복사 후 사용 |
| `_` 접두사 규칙 | 내부 운영/보조 폴더에 사용 (`_workspace/`, `_assets/`) |
| `_workspace/` 네이밍 | `_project/` 변경 검토했으나 `PROJECT.md`와 혼동 우려로 유지 |
| AI CLI 지침 파일 | `CLAUDE.md` 기준, 다른 CLI 사용 시 복사 후 rename |
| 커스텀 명령어 관리 | `_workspace/commands/` 파일 기반 동적 참조 (CLAUDE.md에 목록 하드코딩 불필요) |
| 문서 작성 언어 | 한국어 (코드 주석, 파일명, 명령어는 영어 유지) |
| git commit/push | 사용자가 VSCode UI로 직접 수행, AI CLI는 메시지만 제안 |
| WORKSPACE_GUIDE.md | 폐기 결정 → CLAUDE.md로 통합 |

### 2.2. 2차 세션 — 워크스페이스 가이드 문서 작성 및 AI CLI 지침 정비

> 참조: `_workspace/sessions/260605-201612_session-handoff.md`

**배경**

워크스페이스의 역할과 목적을 사용자가 명확히 파악할 수 있는 별도 가이드 문서가 필요했다. 또한 Claude Code와 Codex가 동일한 운영 규칙을 따르도록 지침 파일 동기화 방안을 마련했다.

**신규 생성 파일**

| 파일 | 내용 |
| --- | --- |
| `AGENTS.md` | Codex 용 AI CLI 운영 지침 (CLAUDE.md와 동일 내용) |
| `_workspace/docs/workspace-guide.md` | 워크스페이스 목적, 구조, 사용 흐름, 주의사항 설명 문서 |

**주요 결정사항**

| 항목 | 결정 내용 |
| --- | --- |
| 가이드 파일명 | `workspace-guide.md` (`workspace-usage-guide.md`, `user-guide.md` 등 검토 후 확정) |
| 가이드 위치 | `_workspace/docs/` |
| CLAUDE.md / AGENTS.md | 동일한 내용으로 유지 (`cmp -s`로 검증) |
| 기본 폴더 구조 | `AGENTS.md`, `_workspace/docs/` 를 기본 항목으로 추가 |

### 2.3. 3차 세션 — writing-style.md 개선 및 coding-style.md 분리

> 참조: `_workspace/sessions/260605-213711_session-handoff.md`

**배경**

문서 작성 규칙과 코딩 규칙이 하나의 파일에 혼재되어 있어 관심사를 분리했다. 또한 AI CLI가 문서 스타일을 더 정확하게 적용할 수 있도록 writing-style.md의 규칙을 개선했다.

**신규 생성 파일**

| 파일 | 내용 |
| --- | --- |
| `_workspace/rules/coding-style.md` | 코드 작성 공통 규칙 (writing-style.md에서 분리) |

**수정 파일**

| 파일 | 변경 내용 |
| --- | --- |
| `_workspace/rules/writing-style.md` | 문체 규칙 통일, 불릿 분리 기준 추가 (섹션 2.6), 코딩 스타일 섹션 제거 후 10개 섹션으로 재정렬 |
| `_workspace/docs/workspace-guide.md` | `README.md`, `PROJECT.md`도 writing-style.md 적용 대상임을 섹션 6에 명시 |
| `README.md`, `PROJECT.md` | writing-style.md 규칙 적용 (메타정보 블록, 목차, H2/H3 번호 체계, 서술체) |
| `TASKS.md`, `PROJECT.md` | Stage/Phase 항목 콜론 제거 |
| `_workspace/sessions/260605-061546_session-handoff.md` | `_workspace/prompts/` 경로 잔재 5곳을 `_workspace/commands/`로 수정 |

**주요 결정사항**

| 항목 | 결정 내용 |
| --- | --- |
| writing-style.md 적용 범위 | `README.md`, `PROJECT.md` 포함 명시 |
| 문체 규칙 | 기술/학술 문서 형식으로 단일 기준 통일 (자동 구분 방식 불채택) |
| 불릿 분리 기준 | 독립 항목이 하나의 문단에 있을 때 분리, 연속 서술 시 유지 |
| Stage/Phase 표기 | 콜론 없는 형식 (`Stage 1 {Stage명}`) |
| sync-cli-guides 명령어 | 보류 (CLAUDE.md / AGENTS.md 동기화 방식 미결) |

### 2.4. 4차 세션 — 주제 분류 체계 도입

> 참조: `_workspace/sessions/260605-215637_session-handoff.md`

**배경**

문서 작성, 파일명, 태그 결정 시 공통 기준이 필요하여 9개 subject code로 구성된 주제 분류 체계를 도입했다.

**신규 생성 파일**

| 파일 | 내용 |
| --- | --- |
| `_workspace/rules/subject-classification.md` | subject code 9개 정의 및 분류별 세부 항목 예시 |

**수정 파일**

| 파일 | 변경 내용 |
| --- | --- |
| `_workspace/docs/workspace-guide.md` | "7. 주제 분류 체계" 섹션 추가, 목차 8번으로 확장 |
| `PROJECT.md`, `README.md` | 태그 자리표시자를 `{subject-code}, {tag1}, {tag2}` 형식으로 변경 |

**주요 결정사항**

| 항목 | 결정 내용 |
| --- | --- |
| subject code | MATH, PHYS, NA, ML, CV, NLP, CS, DEV, MISC 9개 |
| 섹션명 언어 정책 | H1·H2는 한국어, H3 주제명(subject name)은 영어 원문 유지 |
| 세부 항목 형식 | 체크박스 없는 일반 목록 (예시 성격) |
| 태그 위치 | subject code를 태그 첫 번째 위치에 배치 |
| 세부 항목 언어 | 전체 영어 (한국어 항목 "pi 계산", "카오스와 프랙탈"을 영어로 수정) |

### 2.5. 5차 세션 — 커스텀 명령어 체계 정비 및 신규 명령어 추가

**배경**

커스텀 명령어 호출 방식이 `/{파일명}` 슬래시 형식으로 정의되어 있었으나 Claude Code 내장 슬래시 명령어 시스템과 충돌하여 동작하지 않았다. 호출 방식을 `{파일명} 실행` 또는 `@{파일명.md} 실행` 으로 변경하고, 세션 시작/종료 및 프로젝트 초기화 명령어를 신규 추가하였다.

**신규 생성 파일**

| 파일 | 내용 |
| --- | --- |
| `_workspace/commands/session-start.md` | 세션 시작 브리핑 명령어 — PROJECT.md / TASKS.md / 직전 핸드오프 읽기 후 현황 요약 출력 |
| `_workspace/commands/session-end.md` | 세션 종료 절차 명령어 — TASKS.md 업데이트, workspace-history.md 갱신, session-handoff 실행 |
| `_workspace/commands/project-init.md` | 프로젝트 초기화 명령어 — 대화형으로 정보 수집 후 PROJECT.md → TASKS.md → README.md 작성/갱신 |

**수정 파일**

| 파일 | 변경 내용 |
| --- | --- |
| `CLAUDE.md` | 섹션 9 커스텀 명령어 호출 방식 변경 및 2가지 호출 방법 명시 |
| `README.md` | 연구/학습 워크스페이스 기준으로 재작성 (개요, 주제 분류, 디렉토리 구조) |
| `_workspace/commands/commit-message.md` | 제목 및 호출 설명에서 슬래시(`/`) 제거 |
| `_workspace/commands/session-handoff.md` | 제목 및 호출 설명에서 슬래시(`/`) 제거 |
| `_workspace/docs/workspace-guide.md` | 섹션 5에 커스텀 명령어 호출 방법 2가지 및 명령어 5개 테이블 추가 |

**주요 결정사항**

| 항목 | 결정 내용 |
| --- | --- |
| 커스텀 명령어 호출 방식 | `/{파일명}` 폐기 → `{파일명} 실행` 또는 `@{파일명.md} 실행` 2가지로 확정 |
| 명령어 파일명 유지 | `commit-message`, `session-handoff` 현행 유지 (변경 검토 후 결정) |
| session-start/end 네이밍 | `session-init/close` 대신 `session-start/end` 채택 (대칭성 및 반복 호출 적합성) |
| session-end 수행 범위 | TASKS.md 업데이트 → workspace-history.md 갱신 → session-handoff 순으로 확정 |
| project-init 출력 순서 | PROJECT.md → TASKS.md → README.md 순으로 확정 |

### 2.6. 6차 세션 — 문서 중복/충돌 해소 및 메타정보 태그→주제 전환

> 참조: `_workspace/sessions/260605-233851_session-handoff.md`

**배경**

루트 필수 파일과 `_workspace/` 내 문서 간 중복 내용 및 충돌을 점검하고, 상위 문서가 하위 문서를 참조하는 구조로 정비했다. 또한 메타정보 블록의 `태그` 항목을 subject 전체명 기반의 `주제` 항목으로 전환했다.

**수정 파일**

| 파일 | 변경 내용 |
| --- | --- |
| `CLAUDE.md` | §3.2 커스텀 명령어 호출 방식 구버전 수정, `workspace-guide.md §5` 참조 추가, 메타정보 `주제` 전환 |
| `AGENTS.md` | 동일 내용으로 완전 동기화 (목차 형식 통일, 호출 방식 수정, `주제` 전환) |
| `README.md` | Subject code 표 제거 → `subject-classification.md` 참조로 교체, 목차 번호 목록으로 수정, `주제` 전환 |
| `PROJECT.md` | 메타정보 `태그` → `주제` 전환 |
| `_workspace/docs/workspace-guide.md` | §7 Subject code 표 제거 → `subject-classification.md` 참조로 교체, `주제` 전환 |
| `_workspace/rules/writing-style.md` | 메타정보 블록 예시 및 설명을 `태그` → `주제` (subject 전체명)로 전환 |
| `_workspace/rules/coding-style.md` | 메타정보 `주제` 전환 |
| `_workspace/rules/subject-classification.md` | 메타정보 `주제` 전환 |
| `_workspace/commands/project-init.md` | 진행 단계 AI 초안 제시 방식으로 변경, Task AI 자동 작성으로 변경, 폴더 구조 확인/생성 절차 추가 (파일 작성 전 단계로 이동), PROJECT.md 템플릿 `주제` 전환 |

**주요 결정사항**

| 항목 | 결정 내용 |
| --- | --- |
| 중복 제거 방식 | Subject code 표는 `subject-classification.md` 단일 출처로 통합, 상위 문서는 참조만 |
| 커스텀 명령어 상세 설명 위치 | `workspace-guide.md §5` 단일 출처, CLAUDE.md/AGENTS.md 는 참조 링크만 |
| 메타정보 `태그` 폐기 | subject 전체명(영어)을 값으로 하는 `주제` 항목으로 전환 |
| `subject-classification.md` 파일명 | `subjects.md`, `subject-list.md` 검토 후 현행 유지 결정 |
| CLAUDE.md / AGENTS.md 동기화 | 내용 완전 동일 유지 (AI CLI 공통 지침이므로 CLI 전용 분기 없음) |

### 2.7. 7차 세션 — project-update 명령어 추가 및 문서 문체 통일

**배경**

프로젝트 진행 중 단편적인 수정 사항을 자유롭게 반영하는 명령어(`project-update`)가 필요하다는 요청이 있었다. 기존 `project-init`은 순서대로 정보를 수집하는 마법사 형태로 진행 중 수정에 적합하지 않았다. 또한 `_workspace/commands/` 내 모든 명령어 파일의 문체가 `writing-style.md` 규칙(`~한다`, `~이다`)과 맞지 않아 일괄 수정하였다. 문서 작성 규칙(문체)을 `CLAUDE.md` / `AGENTS.md` 최상위 지침으로 이동하였다.

**신규 생성 파일**

| 파일 | 내용 |
| --- | --- |
| `_workspace/commands/project-update.md` | 자유 형식 입력으로 PROJECT.md / TASKS.md / README.md 선택적 갱신 |

**수정 파일**

| 파일 | 변경 내용 |
| --- | --- |
| `_workspace/commands/commit-message.md` | 문체 통일 (`~합니다` → `~한다`) |
| `_workspace/commands/project-init.md` | 문체 통일 |
| `_workspace/commands/session-start.md` | 문체 통일 |
| `_workspace/commands/session-end.md` | 문체 통일 |
| `_workspace/commands/session-handoff.md` | 문체 통일 |
| `_workspace/docs/workspace-guide.md` | §5 커스텀 명령어 테이블에 `project-update` 행 추가 |
| `CLAUDE.md` | §9 문서 작성 규칙 신규 추가 (문체 3개 항목), 기존 §9→§10 으로 번호 변경, 목차 갱신 |
| `AGENTS.md` | 동일 내용으로 동기화 |
| `_workspace/rules/writing-style.md` | §4.3 문체에 `CLAUDE.md` / `AGENTS.md §9` 참조 문구 추가 |

**주요 결정사항**

| 항목 | 결정 내용 |
| --- | --- |
| 신규 명령어명 | `project-update` (`project-edit`, `project-patch` 검토 후 확정) |
| project-update 동작 방식 | 자유 형식 입력 → 의도 파악 → 단순 추가는 즉시 반영, 삭제·구조 변경은 확인 후 반영 |
| 문체 규칙 위치 | `writing-style.md` 에서 `CLAUDE.md` / `AGENTS.md §9` 로 이동, writing-style.md 는 참조 |

### 2.8. 8차 세션 — 섹션 번호 형식 변경 및 세션 파일명 오류 수정

> 참조: `_workspace/sessions/260606-071228_session-handoff.md`

**배경**

LaTeX/ACM/Springer 계열 관용에 맞춰 섹션 번호 형식을 통일하고, 과거 세션에서 발생한 핸드오프 파일명 오류(플레이스홀더 미치환)를 수정하였다. 재발 방지를 위해 session-end/session-handoff 명령어에 파일명 작성 지침을 추가하였다. CLAUDE.md/AGENTS.md 동기화 방식은 수동 복사 현행 유지로 결정하였다.

**수정 파일**

| 파일 | 변경 내용 |
| --- | --- |
| 전체 `.md` 파일 (24개) | H2/H3 헤더 번호 형식 변경 (`## 1 제목` → `## 1. 제목`, `### 1.1 제목` → `### 1.1. 제목`) |
| `_workspace/rules/writing-style.md` | §5.1 테이블, §5.2 규칙 설명 및 예시, §2.1 구조 템플릿 코드블록 업데이트 |
| `_workspace/commands/session-end.md` | Step 4에 `date +%y%m%d-%H%M%S` 실행 후 파일명 사용 지침 추가, 플레이스홀더 금지 명시 |
| `_workspace/commands/session-handoff.md` | 저장 위치 섹션에 동일 파일명 지침 추가 |
| `_workspace/docs/workspace-history.md` | 6차 세션 참조 파일명 수정 (`260605-HHMMSS` → `260605-233851`) |
| `_workspace/sessions/260605-HHMMSS_session-handoff.md` | 파일명 수정 → `260605-233851_session-handoff.md` |
| `_workspace/sessions/260606-000000_session-handoff.md` | 파일명 수정 → `260606-001837_session-handoff.md` |

**주요 결정사항**

| 항목 | 결정 내용 |
| --- | --- |
| 섹션 번호 형식 | LaTeX/ACM/Springer 계열 관용 적용 — H2: `1.`, H3: `1.1.`, H4/Stage/Phase: 점 없음 |
| 세션 파일명 시각 기준 | 커밋 시각 기준으로 rename (`date +%y%m%d-%H%M%S` 실행 후 사용) |
| CLAUDE.md/AGENTS.md 동기화 | SSOT 방식(공통 파일 참조) 불채택 — 자동 컨텍스트 로드 필수 조건으로 현행 수동 복사 유지 |

### 2.9. 9차 세션 — 메타정보 형식 변경 및 문서 정비

> 참조: `_workspace/sessions/260606-075523_session-handoff.md`

**배경**

메타정보 날짜 표기를 워크스페이스 공식 형식인 `YYMMDD-HHMMSS`로 통일하고, CLAUDE.md/AGENTS.md SSOT 방식 미채택 근거를 workspace-guide §5에 명시하였다. project-history §1 변경 이력 요약 테이블에 시각 컬럼을 추가하였다.

**수정 파일**

| 파일 | 변경 내용 |
| --- | --- |
| 전체 `.md` 파일 | 메타정보 필드명 `생성일/수정일` → `생성일시/수정일시`, 날짜 형식 `YYYYMMDD` → `YYMMDD` |
| `_workspace/rules/writing-style.md` | §3.2 날짜 형식 규칙 업데이트, §2.1·§2.2 예시 코드블록 형식 반영 |
| `_workspace/docs/workspace-guide.md` | §5에 CLAUDE.md/AGENTS.md 공통 파일 미사용 이유 단락 추가, 메타정보 형식 업데이트 |
| `_workspace/docs/project-history.md` | §1 변경 이력 요약 테이블에 시각 컬럼 추가 (HHMMSS) |
| `_workspace/commands/session-end.md` | Step 3 테이블 작성 형식 `YYYY-MM-DD` → `YYMMDD \| HHMMSS` |

**주요 결정사항**

| 항목 | 결정 내용 |
| --- | --- |
| 메타정보 날짜 형식 | `YYMMDD-HHMMSS` 공식 형식 확정 (기존 파일은 git 커밋 시각 기준 소급 변환) |
| CLAUDE.md/AGENTS.md SSOT 미채택 근거 | workspace-guide §5에 명시 — 외부 파일 참조 시 자동 컨텍스트 로드 불보장 |

### 2.10. 10차 세션 — CLAUDE.md 구조 개편 및 개조식 원칙 전면 적용

> 참조: `_workspace/sessions/260607-074159_session-handoff.md`

**배경**

문서 작성 규칙이 워크스페이스의 절대 원칙임을 강조하기 위해 CLAUDE.md 섹션 순서를 재구성하였다. AI CLI 응답 스타일 규칙을 문서 작성 규칙과 분리하여 신규 섹션으로 독립시켰다. 개조식 항목 작성 원칙을 CLAUDE.md 전체에 적용하고 AGENTS.md 와 동기화하였다. README.md 를 프로젝트 전용 템플릿으로 교체하고, 기존 워크스페이스 소개 내용은 workspace-readme.md 로 분리하였다.

**신규 생성 파일**

| 파일 | 내용 |
| --- | --- |
| `_workspace/docs/workspace-readme.md` | 기존 README.md 의 워크스페이스 소개 내용 이전 |
| `_workspace/docs/project-dashboard.md` | 프로젝트 대시보드 문서 (신규) |

**수정 파일**

| 파일 | 변경 내용 |
| --- | --- |
| `README.md` | 워크스페이스 소개 제거 → 프로젝트 전용 템플릿으로 교체 |
| `TASKS.md` | 메타정보 블록 추가 |
| `CLAUDE.md` | 섹션 순서 재구성(11개), §2 문서 작성 규칙 앞으로 이동, §3 AI CLI 응답 스타일 신설, 전체 항목 개조식 적용 |
| `AGENTS.md` | CLAUDE.md 최종 상태와 완전 동기화 |
| 전체 `.md` (19개) | `---` 구분선 일괄 제거 |

**주요 결정사항**

| 항목 | 결정 내용 |
| --- | --- |
| 문서 작성 규칙 위치 | §2 로 앞으로 이동 — 워크스페이스 절대 원칙임을 구조로 강조 |
| AI CLI 응답 스타일 분리 | §3 신설 — 경어체 응답, 이모지 금지, 불필요한 사과/서두 금지 (문서 작성 규칙과 별개) |
| 개조식 항목 규칙 | `항목명: 설명` 은 대상 구분이 필요할 때만 사용, 나머지는 설명만 |
| `---` 구분선 | GitHub 마크다운 자동 구분선과 중복 → 전체 문서에서 일괄 제거 |
| README.md 역할 분리 | 루트 README.md 는 프로젝트 전용, 워크스페이스 소개는 workspace-readme.md 로 분리 |
