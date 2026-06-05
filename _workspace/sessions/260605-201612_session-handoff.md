# 워크스페이스 사용 가이드 정리 세션 핸드오프

> 작성일시: 260605-202038
> 세션 목적: 워크스페이스의 역할과 목적을 분석하고, 사용자용 가이드 문서와 AI CLI 지침 파일 구조를 정리
> 이전 핸드오프: 260605-061546_session-handoff.md

---

## 1. 세션 핵심 요약

- 사용자가 현재 워크스페이스의 역할과 목적 분석을 요청했다.
- `PROJECT.md` 와 `TASKS.md` 를 확인한 결과, 현재 프로젝트 내용은 아직 자리표시자 상태이며 이 저장소는 실제 프로젝트보다 범용 워크스페이스 템플릿 성격이 강하다고 분석했다.
- 워크스페이스의 핵심 역할을 다음 세 가지로 정리했다.
  - AI CLI 협업 운영 기준 제공
  - 프로젝트 실행 흐름 표준화
  - Jupyter Book v2 기반 문서형 산출물 제작 기반 제공
- 사용자가 `_workspace/docs` 에 워크스페이스 사용 목적과 사용법을 상세히 정리하고 싶다고 요청했다.
- 문서 파일명 후보로 `workspace-usage-guide.md`, `workspace-overview.md`, `workspace-operation-guide.md`, `workspace-manual.md`, `workspace-template-guide.md` 를 제안했다.
- 사용자가 `user-guide.md` 를 검토했고, 최종적으로 `workspace-guide.md` 로 확정했다.
- `_workspace/docs/workspace-guide.md` 를 새로 생성했다.
- 사용자가 문서 변경사항 확인을 요청했고, `CLAUDE.md`, `AGENTS.md`, `_workspace/docs/workspace-guide.md` 변경 상태를 확인했다.
- `CLAUDE.md` 와 `AGENTS.md` 는 동일한 내용으로 유지되어야 한다는 사용자의 요구를 반영했다.
- `CLAUDE.md` 와 `AGENTS.md` 의 폴더 구조 예시에 `AGENTS.md` 와 `_workspace/docs/` 를 기본 항목으로 추가했다.
- `cmp -s CLAUDE.md AGENTS.md` 로 두 파일이 완전히 동일함을 확인했다.
- 현재 Git 상태는 `CLAUDE.md` 수정, `AGENTS.md` 신규 파일, `_workspace/docs/` 신규 폴더가 있는 상태이다.

---

## 2. 사용자 요청 및 의도

| 요청 내용 | 배경 목적 |
| --- | --- |
| 이 워크스페이스의 역할과 목적 분석 | 현재 구조가 어떤 의도로 설계되었는지 명확히 파악 |
| `_workspace/docs` 에 분석 내용을 상세 문서로 정리 | 워크스페이스 자체의 사용 목적과 사용법을 별도 운영 문서로 보관 |
| 파일명 제안 | 새 문서의 성격과 범위를 명확히 표현하는 이름 선택 |
| `user-guide.md` 검토 | 사람이 읽는 대표 사용 설명서로 적절한지 판단 |
| `workspace-guide.md` 로 확정 | 워크스페이스 자체의 가이드임을 명확히 드러내기 위함 |
| 문서 변경사항 확인 | 생성/수정된 문서와 Git 상태를 점검 |
| `CLAUDE.md` 와 `AGENTS.md` 를 동일하게 유지 | Claude Code 와 Codex 가 같은 워크스페이스 운영 규칙을 따르도록 보장 |
| 폴더 구조에 `CLAUDE.md`, `AGENTS.md` 2개 파일을 기본 반영 | 템플릿 복사 시 두 AI CLI 지침 파일을 기본 구성으로 포함 |

---

## 3. 확정된 결정사항

| 항목 | 확정 내용 | 비고 |
| --- | --- | --- |
| 워크스페이스 성격 | 특정 프로젝트가 아니라 AI CLI 협업용 범용 워크스페이스 템플릿 | 현재 `PROJECT.md`, `TASKS.md` 는 자리표시자 상태 |
| 사용자 가이드 파일명 | `_workspace/docs/workspace-guide.md` | 사용자가 최종 확정 |
| 사용자 가이드 위치 | `_workspace/docs/` | 워크스페이스 자체의 사용법과 운영 문서 보관 위치 |
| 사용자 가이드 내용 범위 | 목적, 핵심 구조, 기본 사용 흐름, AI CLI 사용 방식, 문서 산출물 관리, 주의사항 | 실제 프로젝트 설명이 아니라 템플릿 사용법 중심 |
| AI CLI 지침 파일 | `CLAUDE.md` 와 `AGENTS.md` 를 동일한 내용으로 유지 | Claude Code 와 Codex 모두 같은 규칙 사용 |
| 기본 루트 파일 | `CLAUDE.md` 와 `AGENTS.md` 를 둘 다 기본 구조에 포함 | 폴더 구조 예시에 반영 완료 |
| `_workspace/docs/` | 기본 폴더 구조에 포함 | `CLAUDE.md`, `AGENTS.md`, `workspace-guide.md` 에 반영 |
| Git commit/push | AI CLI 는 수행하지 않음 | 기존 운영 규칙 유지 |

---

## 4. AI 핵심 제안 및 분석

- **워크스페이스 역할 분석**
  - `PROJECT.md`, `TASKS.md`, `README.md` 가 모두 자리표시자 상태임을 근거로 실제 프로젝트보다 템플릿 저장소로 해석했다.
  - `_workspace/commands/`, `_workspace/rules/`, `_workspace/sessions/`, `docs/myst.yml` 구조를 근거로 AI CLI 협업과 문서 산출물 제작을 핵심 용도로 분석했다.

- **파일명 후보 제안**
  - 최초 추천은 `workspace-usage-guide.md` 였다.
  - 사용자가 `user-guide.md` 를 물었을 때 사람이 읽는 대표 설명서로는 적절하지만, 여러 운영 문서가 늘어날 경우 범위가 모호할 수 있다고 설명했다.
  - 최종적으로 사용자가 `workspace-guide.md` 를 선택했고, 해당 이름으로 문서를 생성했다.

- **문서 내용 설계**
  - `_workspace/docs/workspace-guide.md` 는 `_workspace/rules/writing-style.md` 의 문서 스타일에 맞춰 한국어 서술체로 작성했다.
  - 메타정보 블록, 목차, 번호형 H2 구조를 포함했다.
  - 데이터 흐름은 `_assets/ -> scripts/ -> outputs/ -> docs/contents/` 로 정리했다.

- **AI CLI 지침 파일 동기화**
  - `CLAUDE.md` 와 `AGENTS.md` 는 같은 운영 지침이어야 한다는 사용자 요청에 따라 동일 내용으로 맞췄다.
  - 두 파일의 폴더 구조 예시에 `AGENTS.md` 와 `_workspace/docs/` 를 추가했다.
  - `cmp -s CLAUDE.md AGENTS.md` 명령으로 두 파일이 완전히 동일함을 확인했다.

---

## 5. 미결 사항

| # | 항목 | 현재 상태 | 결정 필요 내용 |
| --- | --- | --- | --- |
| 1 | `PROJECT.md` 실제 내용 작성 | 자리표시자 상태 | 이 템플릿 자체의 프로젝트 명세로 채울지, 복사용 템플릿이므로 비워둘지 결정 필요 |
| 2 | `TASKS.md` 실제 작업 목록 작성 | 자리표시자 상태 | 템플릿 개선 작업 목록을 관리할지 결정 필요 |
| 3 | `.gitignore` 템플릿 작성 | 이전 핸드오프에서 다음 작업으로 남아 있음 | `docs/_build/`, Python 캐시, OS 파일, 필요 시 `outputs/` 포함 여부 결정 |
| 4 | `docs/myst.yml` 보완 | 기본값 상태 | 실제 Jupyter Book v2 템플릿으로 충분한지 검토 필요 |
| 5 | `README.md` 갱신 | 자리표시자 상태 | 이 저장소를 워크스페이스 템플릿으로 소개하도록 작성할지 결정 필요 |
| 6 | 줄바꿈 형식 | `CLAUDE.md` diff 시 `LF will be replaced by CRLF` 경고 확인 | `.gitattributes` 또는 에디터 설정으로 통일할지 결정 필요 |

---

## 6. 다음 작업 목록

| 우선순위 | 작업 | 관련 폴더/파일 | 사용할 도구 |
| --- | --- | --- | --- |
| 1 | `workspace-guide.md` 내용을 사용자가 검토하고 필요한 표현을 수정 | `_workspace/docs/workspace-guide.md` | Codex / VSCode |
| 2 | `CLAUDE.md` 와 `AGENTS.md` 가 이후에도 동일하게 유지되는지 변경 전후 확인 | `CLAUDE.md`, `AGENTS.md` | `cmp -s CLAUDE.md AGENTS.md` |
| 3 | `.gitignore` 템플릿 작성 | `.gitignore` | Codex |
| 4 | `README.md` 를 워크스페이스 템플릿 소개 문서로 갱신 | `README.md` | Codex |
| 5 | `PROJECT.md`, `TASKS.md` 를 템플릿 자체 관리용으로 채울지 결정 | `PROJECT.md`, `TASKS.md` | 사용자 결정 후 Codex |
| 6 | 필요 시 `_workspace/docs/workspace-guide.md` 를 `README.md` 또는 `CLAUDE.md` 에서 참조하도록 링크 추가 | `README.md`, `CLAUDE.md`, `AGENTS.md` | Codex |

---

## 7. 다음 세션에서 이어받기

### 새 세션 시작 지시문:

"아래는 이전 세션의 컨텍스트입니다.
이 내용을 기반으로 워크스페이스 템플릿 정리를 이어서 진행해 주세요.

현재까지 확정된 내용:
1. 이 저장소는 AI CLI 협업용 범용 워크스페이스 템플릿이다.
2. 사용자용 워크스페이스 가이드는 `_workspace/docs/workspace-guide.md` 로 작성했다.
3. `CLAUDE.md` 와 `AGENTS.md` 는 동일한 내용으로 유지해야 한다.
4. 기본 폴더 구조에는 `CLAUDE.md`, `AGENTS.md`, `_workspace/docs/` 가 포함되어야 한다.

우선적으로 다음 작업을 진행해 주세요:
1. 현재 Git 변경사항을 확인한다.
2. `workspace-guide.md` 의 표현과 구조를 검토한다.
3. 필요하면 `README.md` 를 워크스페이스 템플릿 소개 문서로 갱신한다.
4. `.gitignore` 템플릿 작성을 검토한다.
5. `CLAUDE.md` 와 `AGENTS.md` 가 여전히 동일한지 확인한다."

---

## 8. 참고 자료 및 링크

| 항목 | 위치/경로 | 용도 |
| --- | --- | --- |
| 이전 핸드오프 | `_workspace/sessions/260605-061546_session-handoff.md` | 최초 워크스페이스 템플릿 설계 맥락 |
| 워크스페이스 사용자 가이드 | `_workspace/docs/workspace-guide.md` | 워크스페이스 목적과 사용법 설명 |
| Claude Code 지침 파일 | `CLAUDE.md` | Claude Code 용 AI CLI 운영 지침 |
| Codex 지침 파일 | `AGENTS.md` | Codex 용 AI CLI 운영 지침 |
| 커스텀 명령어 정의 | `_workspace/commands/session-handoff.md` | `/session-handoff` 작성 규칙 |
| 커밋 메시지 명령어 정의 | `_workspace/commands/commit-message.md` | `/commit-message` 작성 규칙 |
| 문서 작성 스타일 | `_workspace/rules/writing-style.md` | 기술/학술 문서 작성 규칙 |
| Jupyter Book 설정 | `docs/myst.yml` | 최종 문서 빌드 설정 |
