# 워크스페이스 템플릿 설계 세션 핸드오프

> 작성일시: 260605-195326
> 세션 목적: GitHub 연계 로컬 워크스페이스의 공통 폴더 구조 / 필수 파일 / 운영 규칙 설계 및 템플릿 파일 생성
> 이전 핸드오프: 없음 (최초 세션)

---

## 1. 세션 핵심 요약

- GitHub 연계 로컬 워크스페이스에서 AI CLI (Claude Code / Codex / RooCode) 를 활용한 프로젝트 수행을 위한 공통 템플릿 설계
- 딥러닝/ML 에서 출발했으나 범용 구조로 확장 (디자인 패턴의 추상 인터페이스 개념 적용)
- 필수 파일 4개 (README.md, PROJECT.md, TASKS.md, CLAUDE.md) 확정 및 템플릿 작성
- 폴더 구조 확정 및 `workspace-template/` 폴더로 구성 완료
- `_` 접두사 규칙 (내부 운영/보조 폴더) 확정
- WORKSPACE_GUIDE.md 폐기 결정 → CLAUDE.md 로 통합
- 커스텀 명령어 프롬프트 파일 2개 작성 완료

---

## 2. 사용자 요청 및 의도

| 요청 내용 | 배경 목적 |
| --- | --- |
| 폴더 구조 / 필수 파일 정의 | AI CLI 와 반복 작업 시 공통 뼈대로 재사용 |
| 범용 구조로 설계 | 딥러닝뿐 아니라 문서 작성 등 다양한 프로젝트에 적용 |
| WORKSPACE_GUIDE.md 설계 | AI CLI 초기화 지침서로 활용 예정이었으나 템플릿 복사 방식으로 대체 |
| 템플릿 폴더 복사 방식 채택 | 매번 AI CLI 로 구조 생성하는 것보다 효율적 |
| 커스텀 명령어 프롬프트 파일 통합 | 기존 보유 프롬프트를 현재 문서 스타일에 맞게 재작성 |

---

## 3. 확정된 결정사항

| 항목 | 확정 내용 | 비고 |
| --- | --- | --- |
| 프로젝트 유형 | 범용 (딥러닝/ML + 문서 작성 포함) | 프로젝트별 확장 가능 |
| GitHub 연계 | 단일 계정 / 단일 레포 | |
| 시작 방식 | 워크플로우 A (GitHub 우선) 또는 B (로컬 우선) | 결과 구조 동일 |
| 초기화 방식 | `workspace-template/` 복사 후 사용 | WORKSPACE_GUIDE.md 폐기 |
| AI CLI 컨텍스트 파일 | `CLAUDE.md` (다른 CLI 사용 시 복사 후 rename) | AGENTS.md / GEMINI.md / ROO.md |
| 필수 파일 | README.md, PROJECT.md, TASKS.md, CLAUDE.md | 한국어 제목/섹션명 |
| `_` 접두사 규칙 | 내부 운영/보조 폴더에 사용 | `_workspace/`, `_assets/` |
| `_workspace/` 유지 | `_project/` 로 변경 검토했으나 유지 결정 | PROJECT.md 와 혼동 우려 |
| `outputs/` 하위 구조 | 하위 폴더 없이 단순화 | 프로젝트별 필요 시 추가 |
| 문서 최종 산출물 | `docs/` (Jupyter Book v2 배포 가능) | |
| 용어 사용 기준 | 워크스페이스=환경/구조, 프로젝트=작업내용 | 혼용 허용, CLAUDE.md 에 명시 |
| 커스텀 명령어 관리 | `_workspace/commands/` 파일 기반 동적 참조 | CLAUDE.md 에 목록 불필요 |
| 문서 작성 언어 | 한국어 (코드 주석 / 파일명 / 명령어는 영어 유지) | |
| 세션 핸드오프 파일명 | `YYMMDD-HHMMSS_session-handoff.md` | |
| git commit/push | 사용자가 VSCode UI 로 직접 수행 | AI CLI 는 메시지만 제안 |

---

## 4. AI 핵심 제안 및 분석

- **범용 인터페이스 구조 적용**
  - 딥러닝 특화 구조에서 출발했으나 디자인 패턴의 추상 인터페이스 개념을 적용하여 범용화
  - `src/`, `tests/`, `configs/` 를 기본 구조에서 제외하고 프로젝트별 추가 방식 채택

- **`_` 접두사 규칙**
  - Python 관행 및 Jupyter Book (`_build/`, `_static/`) 관행과 일관성 확보
  - 파일 탐색기에서 맨 앞 정렬로 접근 편의성 확보

- **WORKSPACE_GUIDE.md 폐기 결정**
  - 초기 설계: AI CLI 가 읽고 구조 자동 생성
  - 변경: 템플릿 폴더 복사 방식이 더 효율적
  - CLAUDE.md 와 역할 중복 → CLAUDE.md 로 통합

- **`_workspace/` 네이밍 유지**
  - `_project/` 변경 검토: `PROJECT.md` 와 혼동 가능성 및 `commands/` 성격이 환경(워크스페이스) 에 가까움

- **커스텀 명령어 동적 참조 방식**
  - CLAUDE.md 에 명령어 목록 하드코딩 대신 `_workspace/commands/` 폴더를 단일 소스로 참조
  - 새 프롬프트 파일 추가만으로 명령어 자동 확장

---

## 5. 미결 사항

| # | 항목 | 현재 상태 | 결정 필요 내용 |
| --- | --- | --- | --- |
| 1 | `.gitignore` 처리 범위 | 추후 논의로 연기 | `outputs/`, `docs/_build/` 등 제외 항목 확정 |
| 2 | `outputs/` 하위 구조 | 미정 | 실험 관리 도구 결정 후 `interim/`, `final/` 추가 여부 |
| 3 | Python 환경 세팅 규칙 | 미논의 | conda env 명명 규칙 등 CLAUDE.md 추가 여부 |
| 4 | GitHub Actions CI/CD | 미논의 | 포함 여부 결정 필요 |
| 5 | `docs/contents/chap01/` 기본 파일 | 미논의 | `index.md` 등 기본 파일 포함 여부 |

---

## 6. 다음 작업 목록

| 우선순위 | 작업 | 관련 폴더/파일 | 사용할 도구 |
| --- | --- | --- | --- |
| 1 | `.gitignore` 템플릿 작성 | `workspace-template/.gitignore` | Claude 대화 |
| 2 | `docs/contents/chap01/index.md` 기본 파일 추가 | `workspace-template/docs/contents/chap01/` | Claude 대화 |
| 3 | `docs/myst.yml` 내용 검토 및 보완 | `workspace-template/docs/myst.yml` | Claude 대화 |
| 4 | Python 환경 세팅 규칙 CLAUDE.md 추가 여부 결정 | `workspace-template/CLAUDE.md` | Claude 대화 |
| 5 | 실제 프로젝트에 템플릿 적용 테스트 | 신규 레포 | Claude Code / VSCode |

---

## 7. 다음 세션에서 이어받기

### 새 세션 시작 지시문:

"아래는 이전 세션의 컨텍스트입니다.
이 내용을 기반으로 워크스페이스 템플릿 설계를 이어서 진행해 주세요.

현재까지 완성된 산출물:
- `workspace-template/` 폴더 구조 및 필수 파일 4개 완성
- `_workspace/commands/session-handoff.md`, `commit-message.md` 완성
- 모든 파일 한국어로 작성 완료

우선적으로 다뤄주세요:
1. `.gitignore` 템플릿 작성
2. `docs/contents/chap01/index.md` 기본 파일 추가
3. `docs/myst.yml` 내용 검토 및 보완"

---

## 8. 참고 자료 및 링크

| 항목 | 위치/경로 | 용도 |
| --- | --- | --- |
| 템플릿 폴더 | `workspace-template/` | 신규 프로젝트 시작 시 복사 |
| AI CLI 운영 지침 | `workspace-template/CLAUDE.md` | 다른 CLI 사용 시 복사 후 rename |
| 세션 핸드오프 프롬프트 | `workspace-template/_workspace/commands/session-handoff.md` | `/session-handoff` 명령어 참조 |
| 커밋 메시지 프롬프트 | `workspace-template/_workspace/commands/commit-message.md` | `/commit-message` 명령어 참조 |