# 워크스페이스 가이드

이 파일은 AI CLI 가 워크스페이스에서 작업할 때 따르는 운영 지침이다.
프로젝트 내용 및 진행 사항은 PROJECT.md 와 TASKS.md 를 참조한다.

다른 AI CLI 사용 시 이 파일을 복사하여 해당 CLI 의 지침 파일명으로 rename 한다.
- Claude: CLAUDE.md
- Codex: AGENTS.md
- Gemini: GEMINI.md
- RooCode: ROO.md

> 생성일: 2026-06-05
> 수정일: 2026-06-05
> 주제: Development Environment and Tools

---

**목차**

1. [용어 정의](#1-용어-정의)
2. [프로젝트 구조](#2-프로젝트-구조)
3. [폴더 규칙](#3-폴더-규칙)
4. [네이밍 규칙](#4-네이밍-규칙)
5. [코딩 컨벤션](#5-코딩-컨벤션)
6. [작업 방식](#6-작업-방식)
7. [Jupyter Book v2](#7-jupyter-book-v2)
8. [제한 사항](#8-제한-사항)
9. [문서 작성 규칙](#9-문서-작성-규칙)
10. [커스텀 명령어](#10-커스텀-명령어)

---

## 1. 용어 정의

이 문서에서 사용하는 용어의 기준이다.
사용자는 두 용어를 혼용할 수 있으며, 문맥에 따라 같은 대상을 가리킨다.

| 용어 | 의미 | 주로 사용되는 맥락 |
|------|------|-----------------|
| 워크스페이스 | 작업 환경/공간 (폴더 구조, 운영 규칙, AI CLI 설정) | 폴더 구조, CLAUDE.md, `_workspace/` |
| 프로젝트 | 수행하는 작업 내용 (목적, 범위, 단계, 산출물) | PROJECT.md, TASKS.md, 작업 명세 |

---

## 2. 프로젝트 구조

```
project-root/
├── README.md                   # 프로젝트 외부 소개
├── PROJECT.md                  # 프로젝트 내부 명세
├── TASKS.md                    # Stage-Phase-Task 진행 관리
├── CLAUDE.md                   # AI CLI 워크스페이스 운영 지침 (이 파일)
├── AGENTS.md                   # Codex 용 AI CLI 워크스페이스 운영 지침
├── _workspace/                 # 워크스페이스 운영 관리
│   ├── commands/               # 커스텀 명령어 프롬프트
│   ├── docs/                   # 워크스페이스 사용법 및 운영 문서
│   ├── rules/                  # 워크스페이스 공통 규칙
│   └── sessions/               # 세션 핸드오프 문서
├── _assets/                    # 읽기 전용 입력 보관소
├── scripts/                    # 실행 스크립트 및 Python 파일
├── outputs/                    # 프로젝트 산출물
└── docs/                       # 최종 산출물 (Jupyter Book v2)
    ├── myst.yml
    └── contents/
        └── chap01/
            └── images/
```

---

## 3. 폴더 규칙

### 3.1. 접두사 규칙

| 접두사 | 의미 | 예시 |
|--------|------|------|
| `_` | 내부 운영/보조 폴더 (프로젝트 산출물 아님) | `_workspace/`, `_assets/` |
| 없음 | 프로젝트 산출물 또는 표준 폴더 | `docs/`, `scripts/`, `outputs/` |

### 3.2. 폴더 역할

| 폴더 | 역할 | 비고 |
|------|------|------|
| `_workspace/` | 워크스페이스 운영 문서 및 세션 기록 | |
| `_workspace/commands/` | 커스텀 명령어 정의 파일 | `{파일명} 실행` 또는 `@{파일명.md} 실행` 형식으로 호출 |
| `_workspace/rules/` | 워크스페이스 공통 규칙 파일 | 문서 작성 스타일 등 |
| `_assets/` | 읽기 전용 입력 보관소 | 참조만 가능, 수정/가공 금지 |
| `scripts/` | 실행 스크립트 및 Python 파일 | 문서 생성 스크립트 포함 |
| `outputs/` | 프로젝트 산출물 | 하위 구조는 프로젝트별 추가 |
| `docs/` | Jupyter Book v2 배포 가능한 최종 산출물 | |

### 3.3. 데이터 흐름

```
_assets/          →      scripts/       →      outputs/
(읽기 전용 입력)           (처리/실행)           (중간/최종 산출물)
                                                    ↓
                                             docs/contents/
                                             (최종 문서)
```

---

## 4. 네이밍 규칙

- 폴더명: 소문자, 하이픈 구분 (예: `chap01`, `session-handoff`)
- 루트 레벨 MD 파일: 대문자 (예: `README.md`, `CLAUDE.md`)
- Python 파일: 소문자, 언더스코어 구분 (예: `train_model.py`)
- 챕터 폴더: `chap01`, `chap02`, ... (두 자리 숫자, 0 패딩)
- 세션 핸드오프 파일: `YYMMDD-HHMMSS_session-handoff.md`

---

## 5. 코딩 컨벤션

- 언어: Python 우선
- 경로 표기: `os.path` 방식 사용 (`pathlib.Path` 사용 금지)
- 코드 내 주석: 영어로 작성
- 들여쓰기: 스페이스 4칸
- 인코딩: UTF-8

---

## 6. 작업 방식

1. 작업 시작 전 `PROJECT.md` 와 `TASKS.md` 를 읽고 현재 진행 상황을 파악한다.
2. 작업 완료 후 `TASKS.md` 의 해당 Task 체크박스를 업데이트한다.
3. `_assets/` 의 파일은 참조만 한다. 수정하거나 가공하지 않는다.
4. 생성된 산출물은 `outputs/` 에 저장한다.
5. 문서에 포함되는 이미지는 `docs/contents/chapXX/images/` 에 저장한다.

---

## 7. Jupyter Book v2

- 설정 파일 위치: `docs/myst.yml`
- 문서 내용 위치: `docs/contents/chapXX/`
- 문서에 포함되는 이미지: `docs/contents/chapXX/images/`
- 빌드 결과물 (`docs/_build/`) 은 `.gitignore` 처리

---

## 8. 제한 사항

- `_assets/` 내 파일 수정 및 삭제 금지
- 루트 레벨 필수 파일 (`README.md`, `PROJECT.md`, `TASKS.md`, `CLAUDE.md`) 임의 삭제 금지
- `docs/_build/` 폴더 직접 생성 금지 (빌드는 사용자가 직접 실행)
- 실제 git commit 및 push 수행 금지 (사용자가 VSCode UI 로 진행)
- 불필요한 사과나 서두 없이 바로 작업을 수행한다.

---

## 9. 문서 작성 규칙

- 본문은 서술체(`~이다`, `~한다`)를 사용한다.
- 경어체(`~입니다`, `~합니다`), 이모지, 불필요한 강조(볼드, 이탤릭)의 남용은 금지한다.
- 상세한 기술 문서 또는 전문적인 학술 문서 형식으로 작성한다.
- 세부 규칙은 `_workspace/rules/writing-style.md` 를 참조한다.

---

## 10. 커스텀 명령어

커스텀 명령어는 `_workspace/commands/` 에 저장된 Markdown 파일로 정의된다.
아래 두 가지 방법으로 호출하면, 해당 파일의 내용을 프롬프트로 실행한다.

- 방법 1: `{파일명 (확장자 제외)} 실행`
- 방법 2: `@{파일명.md} 실행`
- 정의 파일 위치: `_workspace/commands/`
- 새 명령어 추가 시 `_workspace/commands/` 에 Markdown 파일을 추가하면 즉시 사용 가능하다.

호출 예시:

```
project-init 실행
@project-init.md 실행
```

현재 등록된 커스텀 명령어 목록은 `_workspace/commands/` 폴더를 확인한다.
명령어별 상세 설명은 `_workspace/docs/workspace-guide.md` §5 를 참조한다.

> 다른 AI CLI 사용 시에도 동일하게 적용된다.
> `_workspace/commands/` 폴더의 파일명과 내용을 참조하여 동일한 방식으로 명령어를 처리한다.
