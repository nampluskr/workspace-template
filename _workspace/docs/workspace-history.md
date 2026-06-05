# 워크스페이스 변경 이력

이 문서는 워크스페이스 템플릿의 설계 변경 및 주요 결정사항을 시간 순서로 기록한다.
각 항목은 세션 핸드오프 문서를 기반으로 작성하며, 향후 설계 방향 파악과 의사결정 근거 추적에 활용한다.

> 생성일: 2026-06-05
> 수정일: 2026-06-05
> 태그: DEV, workspace, history, changelog

---

**목차**

1. [변경 이력 요약](#1-변경-이력-요약)
2. [세션별 상세 내역](#2-세션별-상세-내역)

---

## 1 변경 이력 요약

| 날짜 | 세션 | 주요 변경 내용 |
| --- | --- | --- |
| 2026-06-05 | 1차 | 워크스페이스 템플릿 최초 설계 및 필수 파일 생성 |
| 2026-06-05 | 2차 | 워크스페이스 가이드 문서 신규 작성 및 AI CLI 지침 파일 정비 |
| 2026-06-05 | 3차 | writing-style.md 개선 및 coding-style.md 분리 |
| 2026-06-05 | 4차 | 주제 분류 체계(subject-classification.md) 도입 |

---

## 2 세션별 상세 내역

### 2.1 1차 세션 — 워크스페이스 템플릿 최초 설계

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

---

### 2.2 2차 세션 — 워크스페이스 가이드 문서 작성 및 AI CLI 지침 정비

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

---

### 2.3 3차 세션 — writing-style.md 개선 및 coding-style.md 분리

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

---

### 2.4 4차 세션 — 주제 분류 체계 도입

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
