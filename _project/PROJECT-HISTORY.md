# 워크스페이스 템플릿 진행 이력

이 문서는 프로젝트의 Stage - Phase - Task 단위 실제 진행 내용을 기록한다.
PROJECT-TODO.md 체크박스 항목과 1:1 대응하며, 완료된 Task 에만 내용을 기입한다.
미완료 또는 미착수 Task 는 헤더를 포함하여 전체 항목을 생략한다.

> 생성일시: 260607-162454
> 수정일시: 260607-162454
> 주제: Development Environment and Tools

## Stage 1 워크스페이스 기반 구축

### Phase 1.1 프로젝트 운영 파일 정비

#### [x] CLAUDE.md / AGENTS.md 운영 지침 작성

> 참조 세션: `_project/sessions/260607-135501_session-handoff.md`

**진행 내용**

AI CLI 운영 지침 파일을 작성하고 구조를 정비하였다.
- CLAUDE.md 전체 섹션 구성 — 문서 작성 규칙, 응답 스타일, 프로젝트 구조, 폴더/네이밍/코딩 규칙, 작업 방식, 커스텀 명령어
- AGENTS.md를 CLAUDE.md와 동일 내용으로 유지
- _workspace/ → _project/ 폴더명 변경 및 전체 참조 수정

**산출물**

| 파일/산출물 | 내용 |
| --- | --- |
| `CLAUDE.md` | Claude Code 용 AI CLI 운영 지침 |
| `AGENTS.md` | Codex 용 AI CLI 운영 지침 (CLAUDE.md 동일 내용) |

#### [x] _project/rules/markdown-style.md 세부 규칙 작성

> 참조 세션: `_project/sessions/260607-135501_session-handoff.md`

**진행 내용**

문서 작성 세부 규칙을 정의하였다.
- 헤더 계층, 수식, 이미지, 테이블, Jupyter Book(MyST) 형식 규칙 작성
- §9.7 admonition 블록 지침 추가 (260607-151653 세션)

**산출물**

| 파일/산출물 | 내용 |
| --- | --- |
| `_project/rules/markdown-style.md` | 통합 Markdown 스타일 가이드 |

#### [x] _project/rules/subjects.md 주제 분류 체계 작성

> 참조 세션: `_project/sessions/260607-135501_session-handoff.md`

**산출물**

| 파일/산출물 | 내용 |
| --- | --- |
| `_project/rules/subjects.md` | 워크스페이스 주제 분류 체계 |

### Phase 1.2 공통 가이드 문서 작성

#### [x] _guides/GUIDES.md 인덱스 작성

> 참조 세션: `_project/sessions/260607-151653_session-handoff.md`

**진행 내용**

가이드 문서 인덱스를 작성하고 관리 체계를 수립하였다.
- 작성 예정/완료 문서 전체 목록 테이블 구성
- 상태 기준(미작성/작성중/완료) 정의

**산출물**

| 파일/산출물 | 내용 |
| --- | --- |
| `_guides/GUIDES.md` | 가이드 문서 인덱스 |

#### [x] _guides/docs/env-spec.md 개발 환경 명세 작성

> 참조 세션: `_project/sessions/260607-151653_session-handoff.md`

**진행 내용**

현재 PC의 하드웨어 및 개발 환경 전체를 실측값 기준으로 문서화하였다.
- §1 요약(하드웨어/OS/개발환경) + §2 하드웨어 + §3 운영체제 + §4 Windows 개발환경 + §5 WSL2 개발환경 구성
- 모든 테이블에 확인일 컬럼 추가
- 개발 환경 구성 확정: Windows(MinGW-w64 + WinPython) / WSL2(Anaconda + g++/gdb) / 공통 IDE(VSCode)

**산출물**

| 파일/산출물 | 내용 |
| --- | --- |
| `_guides/docs/env-spec.md` | 하드웨어·OS·패키지 버전 기준 문서 |

**결정사항**

| 항목 | 결정 내용 |
| --- | --- |
| CUDA 전략 | 시스템 레벨 CUDA Toolkit 미설치, Anaconda 환경별 설치 |
| conda 환경 상세 | env-spec.md에서 제거, conda-env-guide.md에서 별도 관리 |

#### [x] _guides/docs/wsl-setup-guide.md WSL2 환경 구축 가이드 작성

> 참조 세션: `_project/sessions/260607-151653_session-handoff.md`

**진행 내용**

Windows 초기화부터 WSL2 CUDA 환경 구축까지 전체 절차를 문서화하였다.
- Windows 환경 구축(§1) → WSL2 환경 구축(§2) → VSCode WSL 연동(§3) → 설치 확인(§4) 순서
- WSL2 초기화(재설치) 절차 별도 섹션 분리 — Microsoft 저장소 404 오류 대처법 포함
- CUDA 구버전 방식(시스템 CUDA Toolkit + cuDNN 수동 복사)을 admonition으로 추가

**산출물**

| 파일/산출물 | 내용 |
| --- | --- |
| `_guides/docs/wsl-setup-guide.md` | WSL2 환경 재구축 전체 절차 |

#### [x] _guides/docs/cuda-pytorch-guide.md CUDA + PyTorch 환경 구성 가이드 작성

> 참조 세션: `_project/sessions/260607-162454_session-handoff.md`

**진행 내용**

GTX 1080 Ti 환경에서 PyTorch 기반 컴퓨터 비전 작업을 위한 4개 독립 환경 구축 절차를 문서화하였다.
- CUDA 버전 선택 근거 조사 — Pascal(CC 6.1) 지원 제한, PyTorch 2.5.1 기준 CUDA 11.8/12.1 공식 지원
- WinPython 버전 선택 — 3.11.8.0 dot(25.3MB 최소 구성), 3.11 시리즈가 ML 환경에서 가장 안정적
- 4개 환경 각각 독립 완결 섹션으로 구성

파일명 시리즈 수립 과정은 다음과 같다.
- cuda-guide.md 신규 생성 후 cuda-pytorch-guide.md로 rename
- GUIDES.md에 cuda-tensorflow/jax/cupy-guide.md 미작성 항목 추가

**산출물**

| 파일/산출물 | 내용 |
| --- | --- |
| `_guides/docs/cuda-pytorch-guide.md` | CUDA + PyTorch 4개 환경 구성 가이드 |

**결정사항**

| 항목 | 결정 내용 |
| --- | --- |
| CUDA 버전 | 11.8 (레거시 메인) / 12.1 (추가 평가) — PyTorch 2.5.1 동시 지원 마지막 버전 |
| Python 버전 | 3.11 — 2024~2025 ML 환경 기준 가장 안정적으로 검증된 버전 |
| PyTorch 버전 | 2.5.1 — CUDA 11.8과 12.1을 동시에 공식 지원하는 버전 |
| WinPython | 3.11.8.0 dot — slim 없음, dot(최소 구성) 사용, 두 환경 별도 폴더 설치 |
| 파일명 시리즈 | cuda-{framework}-guide.md 패턴으로 통일 |
