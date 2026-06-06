# 워크스페이스 가이드

이 문서는 AI CLI 와 함께 사용하는 범용 워크스페이스 템플릿의 목적, 구조, 사용법을 설명한다.

> 생성일시: 260605-202038
> 수정일시: 260606-115806
> 주제: Development Environment and Tools

**목차**

1. [개요](#1-개요)
2. [사용 목적](#2-사용-목적)
3. [핵심 구조](#3-핵심-구조)
4. [기본 사용 흐름](#4-기본-사용-흐름)
5. [AI CLI 사용 방식](#5-ai-cli-사용-방식)
6. [문서 산출물 관리](#6-문서-산출물-관리)
7. [주제 분류 체계](#7-주제-분류-체계)
8. [사용 시 주의사항](#8-사용-시-주의사항)

## 1. 개요

이 워크스페이스는 특정 프로젝트 하나만을 위한 폴더가 아니라, 여러 프로젝트에서 반복 사용할 수 있는 작업 템플릿이다. 프로젝트의 목적, 진행 상황, 입력 자료, 처리 스크립트, 산출물, 최종 문서를 일관된 구조로 관리하도록 설계되어 있다.

특히 Claude Code, Codex, Gemini, RooCode 같은 AI CLI 와 함께 작업할 때 동일한 규칙을 유지하는 데 초점을 둔다. AI CLI 는 루트의 지침 파일을 읽고, `PROJECT.md` 와 `TASKS.md` 를 기준으로 현재 프로젝트의 목적과 진행 상황을 파악한다.

## 2. 사용 목적

이 워크스페이스의 주요 목적은 다음과 같다.

- 신규 프로젝트를 시작할 때 매번 폴더 구조와 운영 규칙을 새로 설계하지 않고 재사용한다.
- AI CLI 가 작업 맥락을 빠르게 파악할 수 있도록 필수 문서를 표준화한다.
- 입력 자료, 처리 코드, 중간 산출물, 최종 문서를 분리하여 관리한다.
- 세션이 바뀌어도 작업 맥락을 이어받을 수 있도록 핸드오프 문서를 남긴다.
- Jupyter Book v2 기반의 문서형 산출물을 만들 수 있는 기본 구조를 제공한다.

이 구조는 딥러닝, 데이터 분석, 기술 문서 작성, 학습 노트 정리, 연구 자료 정리처럼 입력 자료를 가공하여 문서나 산출물로 만드는 작업에 적합하다.

## 3. 핵심 구조

워크스페이스의 기본 구조는 다음과 같다.

```text
project-root/
├── README.md
├── PROJECT.md
├── TASKS.md
├── CLAUDE.md
├── AGENTS.md
├── _workspace/
│   ├── commands/
│   ├── docs/
│   ├── rules/
│   └── sessions/
├── _assets/
├── scripts/
├── outputs/
└── docs/
    ├── myst.yml
    └── contents/
```

각 파일과 폴더의 역할은 다음과 같다.

| 경로 | 역할 |
| --- | --- |
| `README.md` | 외부 공개용 프로젝트 소개 문서 |
| `PROJECT.md` | 프로젝트의 목적, 배경, 범위, 제약 사항, 단계를 정의하는 내부 명세 |
| `TASKS.md` | Stage - Phase - Task 단위의 진행 현황 관리 문서 |
| `CLAUDE.md` | Claude Code 용 AI CLI 운영 지침 |
| `AGENTS.md` | Codex 용 AI CLI 운영 지침 |
| `_workspace/` | 워크스페이스 운영 문서, 명령어, 규칙, 세션 기록 보관 |
| `_workspace/commands/` | `/session-handoff`, `/commit-message` 같은 커스텀 명령어 정의 |
| `_workspace/docs/` | 워크스페이스 자체의 사용법, 운영 문서, 프로젝트 대시보드 보관. `workspace-readme.md` 는 워크스페이스 템플릿 자체에 대한 소개 문서 |
| `_workspace/rules/` | 문서 작성 스타일 등 공통 규칙 보관 |
| `_workspace/sessions/` | 세션 종료 시 작성하는 핸드오프 문서 보관 |
| `_assets/` | 원본 입력 자료 보관소 |
| `scripts/` | 처리 스크립트와 Python 파일 보관 |
| `outputs/` | 처리 결과와 프로젝트 산출물 보관 |
| `docs/` | Jupyter Book v2 로 배포 가능한 최종 문서 보관 |

## 4. 기본 사용 흐름

새 프로젝트에서 이 템플릿을 사용할 때의 기본 흐름은 다음과 같다.

1. 워크스페이스 템플릿을 새 프로젝트 폴더로 복사한다.
2. `README.md` 에 외부 공개용 프로젝트 소개를 작성한다.
3. `PROJECT.md` 에 프로젝트 목적, 배경, 범위, 제약 사항, 단계를 작성한다.
4. `TASKS.md` 에 Stage - Phase - Task 단위의 작업 목록을 작성한다.
5. 원본 입력 자료는 `_assets/` 에 저장한다.
6. 처리 스크립트는 `scripts/` 에 작성한다.
7. 생성된 중간 산출물이나 결과물은 `outputs/` 에 저장한다.
8. 최종 문서에 포함할 내용은 `docs/contents/` 아래에 정리한다.
9. 세션 종료 전 필요한 경우 `/session-handoff` 명령어로 다음 세션 인수인계 문서를 작성한다.

기본 데이터 흐름은 다음과 같다.

```text
_assets/ -> scripts/ -> outputs/ -> docs/contents/
```

`_assets/` 는 원본 자료 보관소이므로 수정하지 않는다. 가공이 필요한 경우 `scripts/` 에서 처리하고 결과를 `outputs/` 또는 `docs/contents/` 에 저장한다.

## 5. AI CLI 사용 방식

AI CLI 는 작업 시작 시 루트의 지침 파일과 프로젝트 관리 문서를 기준으로 움직인다.

Codex 를 사용할 때는 `AGENTS.md` 를 기준으로 작업한다. Claude Code 를 사용할 때는 `CLAUDE.md` 를 기준으로 작업한다. 다른 AI CLI 를 사용할 때도 같은 내용을 해당 도구의 지침 파일명으로 복사하여 사용할 수 있다.

두 파일은 항상 동일한 내용을 유지해야 한다. 공통 지침 파일을 `_workspace/` 에 두고 참조만 하는 방식도 검토했으나 채택하지 않았다. AI CLI 는 `CLAUDE.md` / `AGENTS.md` 를 세션 시작 시 자동으로 컨텍스트에 로드하지만, 그 안에서 참조하는 외부 파일은 AI 가 명시적으로 Read 도구를 호출해야만 읽힌다. 자동 로드가 보장되지 않으므로 지침 내용을 각 파일에 직접 유지하는 현행 방식을 채택한다. 파일이 2개뿐이므로 수동 동기화 부담도 크지 않다.

AI CLI 에 작업을 요청할 때는 다음 순서를 기준으로 하면 좋다.

1. 먼저 `PROJECT.md` 에 프로젝트의 목적과 범위를 적는다.
2. `TASKS.md` 에 현재 해야 할 일을 체크박스 형태로 적는다.
3. AI CLI 에 특정 Task 를 지정하여 요청한다.
4. 작업 완료 후 AI CLI 가 변경 파일과 확인 내용을 요약하도록 한다.
5. 긴 작업이 끝나면 `_workspace/sessions/` 에 세션 핸드오프 문서를 남긴다.

커스텀 명령어는 `_workspace/commands/` 에 Markdown 파일로 정의한다. 아래 두 가지 방법으로 호출할 수 있다.

- `{파일명 (확장자 제외)} 실행` 예: `session-start 실행`
- `@{파일명.md} 실행` 예: `@session-start.md 실행`

현재 등록된 커스텀 명령어는 다음과 같다.

| 명령어 | 파일 | 수행 내용 |
| --- | --- | --- |
| `session-start` | `_workspace/commands/session-start.md` | 세션 시작 브리핑 — PROJECT.md / TASKS.md / 직전 핸드오프 읽기 후 현황 요약 출력 |
| `session-end` | `_workspace/commands/session-end.md` | 세션 종료 절차 — TASKS.md 업데이트, project-history.md 갱신, session-handoff 실행 |
| `session-handoff` | `_workspace/commands/session-handoff.md` | 세션 핸드오프 문서 작성 및 `_workspace/sessions/` 에 저장 |
| `project-init` | `_workspace/commands/project-init.md` | 대화형으로 프로젝트 정보 수집 후 PROJECT.md → TASKS.md → README.md 작성/갱신 |
| `project-update` | `_workspace/commands/project-update.md` | 자유 형식으로 수정 내용 입력 → PROJECT.md / TASKS.md / README.md 선택적 갱신 |
| `project-status` | `_workspace/commands/project-status.md` | TASKS.md 진행률, 미결 사항, project-history 최근 세션 요약 출력 (읽기 전용) |
| `commit-message` | `_workspace/commands/commit-message.md` | git 변경사항 분석 후 커밋 메시지 제안 |

## 6. 문서 산출물 관리

최종 문서는 `docs/` 에 작성한다. 이 폴더는 Jupyter Book v2 배포를 염두에 둔 구조이다.

```text
docs/
├── myst.yml
└── contents/
    └── chap01/
        ├── index.md
        └── images/
```

문서 작성 시 기본 규칙은 `_workspace/rules/writing-style.md` 를 따른다. 기술 문서와 학술 문서는 한국어 서술체로 작성하고, 코드 주석은 영어로 작성한다. 수식, 명령어, 경로, 파일명은 필요한 경우 영어 또는 LaTeX 를 그대로 사용한다.

이 규칙은 `docs/contents/` 아래의 최종 문서뿐만 아니라 루트의 `README.md` 와 `PROJECT.md` 에도 동일하게 적용한다. 두 파일은 메타정보 블록(`> 생성일시 / 수정일시 / 주제`), 목차, H2/H3 번호 체계를 갖추어야 한다.

문서에 포함되는 이미지는 해당 챕터의 `images/` 폴더에 저장한다. 예를 들어 1장 문서에 들어가는 이미지는 `docs/contents/chap01/images/` 에 저장한다.

## 7. 주제 분류 체계

워크스페이스에서 작성하는 문서, 스크립트, 산출물은 공통 subject 분류를 기준으로 분류한다.
분류 목록, 세부 항목, 활용 방법은 `_workspace/rules/subject-classification.md` 를 참조한다.

## 8. 사용 시 주의사항

이 워크스페이스를 사용할 때의 주의사항은 다음과 같다.

- `_assets/` 안의 원본 파일은 수정하거나 삭제하지 않는다.
- `README.md`, `PROJECT.md`, `TASKS.md`, `CLAUDE.md` 같은 루트 필수 파일은 임의로 삭제하지 않는다.
- `docs/_build/` 는 직접 생성하지 않는다.
- 실제 git commit 과 push 는 사용자가 직접 수행한다.
- AI CLI 는 필요한 경우 커밋 메시지만 제안한다.
- 작업 완료 후 대응되는 항목이 있으면 `TASKS.md` 의 체크박스를 업데이트한다.

현재 템플릿은 실제 프로젝트 내용이 채워지기 전의 기본 상태이다. 따라서 새 프로젝트에 적용할 때는 가장 먼저 `PROJECT.md` 와 `TASKS.md` 의 자리표시자를 실제 내용으로 교체해야 한다.
