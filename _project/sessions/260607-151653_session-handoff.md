# 개발 환경 명세 및 WSL2 구축 가이드 작성 세션 핸드오프

> 작성일시: 260607-151653
> 세션 목적: _guides/docs/ 개발 환경 명세 작성 및 WSL2 환경 구축 가이드 작성
> 이전 핸드오프: 260607-135501_session-handoff.md

## 1. 세션 핵심 요약

- `env-spec.md` 신규 작성 — 하드웨어, 운영체제, Windows/WSL2 개발 환경 명세 전체 작성 및 실제 값 입력
- `wsl-setup-guide.md` 신규 작성 — Windows 초기화부터 WSL2 CUDA 환경 구축까지 전체 절차 문서화
- `markdown-style.md` §9.7 admonition 블록 지침 추가
- `GUIDES.md` wsl-setup-guide.md 상태 완료로 갱신
- 개발 환경 구성 확정: Windows(MinGW-w64 + WinPython) / WSL2(Anaconda + g++/gdb) / 공통 IDE(VSCode)
- CUDA 전략 확정: 시스템 레벨 설치 없이 Anaconda 가상환경별 설치 방식 채택

## 2. 사용자 요청 및 의도

아래 항목은 이 세션에서 처리된 주요 요청과 그 배경이다.

| 요청 내용 | 배경 목적 |
|-----------|-----------|
| env-spec.md 요약 섹션 추가 | 전체 환경을 한눈에 파악하기 위한 인덱스 역할 |
| 개발 환경을 Windows / WSL2 로 분리 | 두 환경이 독립적으로 운용되므로 명확히 구분 필요 |
| 하드웨어 정보 직접 입력 (스크린샷 제공) | 실제 환경 기준 문서화 |
| Visual Studio 제거 | 실제 사용하지 않음 |
| conda 가상환경 상세를 env-spec에서 제거 | conda-env-guide.md 에서 별도 관리 예정 |
| wsl-setup-guide.md 작성 | Windows 초기화 후 환경 재구축 절차 기록 |
| VSCode 설치 및 익스텐션 섹션 추가 | Python/C++ 개발 환경 구성 완성 |
| CUDA 구버전 방식을 admonition으로 추가 | 이전 방식(CUDA Toolkit + cuDNN 수동 복사)과 현재 방식 차이 명시 |
| admonition 블록 문법 지침 추가 | markdown-style.md 규칙으로 공식화 |

## 3. 확정된 결정사항

| 항목 | 확정 내용 | 비고 |
|------|-----------|------|
| 개발 환경 구성 | Windows: MinGW-w64(g++15.2/gdb17.1) + WinPython(3.12/3.10) / WSL2: Anaconda(24.9.2/Python3.12.7) + g++(11.4)/gdb(12.1) | |
| 공통 IDE | VSCode 1.123.0 + WSL 익스텐션 0.104.3 | Windows에만 설치, WSL2는 원격 연결 |
| CUDA 전략 | 시스템 레벨 CUDA Toolkit 미설치, Anaconda 환경별 설치 | nvcc 미설치 상태가 정상 |
| GPU 드라이버 | NVIDIA 572.70, CUDA 최대 지원 12.8 | Windows/WSL2 공유 |
| conda 환경 목록 | base, cupy_env, jax_env, jb2, pytorch_env, tensorflow_env | 상세 구성은 conda-env-guide.md에서 관리 |
| admonition 문법 | `\`\`\`{note}` / `\`\`\`{warning}` 방식 (MyST) | markdown-style.md §9.7에 지침 추가 |
| env-spec.md §5.4 제거 | conda 환경 상세는 conda-env-guide.md로 분리 | |
| 저장장치 | C: NVMe Samsung SSD 980(932GB, OS) / D: ADATA SU800(239GB, 작업공간) | |

## 4. AI 핵심 제안 및 분석

- **env-spec.md 구조 설계**
  - §1 요약(하드웨어/OS/개발환경) + §2 하드웨어 + §3 운영체제 + §4 Windows 개발환경 + §5 WSL2 개발환경으로 분리
  - 모든 테이블에 `확인일` 컬럼 추가 — 정보 갱신 시점 추적 가능

- **CUDA 전략 설명**
  - `nvidia-smi` CUDA Version = 드라이버 지원 최대 버전 (설치 여부와 무관)
  - 구버전 방식(시스템 CUDA Toolkit + cuDNN 수동 복사)의 문제점 명시
  - conda 환경별 설치가 버전 충돌 방지에 유리함을 admonition으로 강조

- **wsl-setup-guide.md 구조**
  - Windows 환경 구축(§1) → WSL2 환경 구축(§2) → VSCode WSL 연동(§3) → 설치 확인(§4) 순서
  - WSL2 초기화(재설치) 절차를 별도 섹션으로 분리 — Microsoft 저장소 404 오류 대처법 포함

## 5. 미결 사항

| # | 항목 | 현재 상태 | 결정 필요 내용 |
|---|------|-----------|----------------|
| 1 | WSL 익스텐션 버전 | 0.104.3 입력 완료, 버전 확인 화면에서 직접 확인 | - |
| 2 | WinPython 3.12 정확한 버전 | WPy64-312101 폴더명으로 유추, python --version 미확인 | WinPython 터미널에서 확인 필요 |
| 3 | conda-env-guide.md | 미작성 | 각 가상환경 용도·패키지 기록 예정 |
| 4 | cuDNN 버전 (WSL2) | 미확인 | 가상환경 구성 시 확인 |

## 6. 다음 작업 목록

| 우선순위 | 작업 | 관련 파일 | 비고 |
|----------|------|-----------|------|
| 1 | conda-env-guide.md 작성 | `_guides/docs/conda-env-guide.md` | GUIDES.md에 미작성 상태 등록됨 |
| 2 | WinPython 3.12 정확한 버전 확인 및 env-spec.md 갱신 | `_guides/docs/env-spec.md` §4.3 | WinPython 터미널에서 `python --version` 실행 |
| 3 | pytorch_env 등 각 conda 환경 구성 | `_guides/docs/conda-env-guide.md` | CUDA Toolkit 포함 설치 |
| 4 | vscode-guide.md 작성 | `_guides/docs/vscode-guide.md` | GUIDES.md에 미작성 상태 등록됨 |

## 7. 다음 세션에서 이어받기

### 새 세션 시작 지시문

"session-start 실행 후 conda-env-guide.md 작성을 진행해 주세요.

각 가상환경(cupy_env, jax_env, jb2, pytorch_env, tensorflow_env)의 용도, 생성 명령, 주요 패키지 설치 절차를 포함합니다.
CUDA Toolkit은 Anaconda 환경별 설치 방식(conda install pytorch-cuda 등)을 기준으로 작성합니다."

## 8. 참고 자료 및 링크

| 항목 | 위치/경로 | 용도 |
|------|-----------|------|
| 개발 환경 명세 | `_guides/docs/env-spec.md` | 하드웨어·OS·패키지 버전 기준 문서 |
| WSL2 구축 가이드 | `_guides/docs/wsl-setup-guide.md` | 환경 재구축 절차 전체 |
| Markdown 스타일 가이드 | `_project/rules/markdown-style.md` | admonition §9.7 추가됨 |
| 가이드 인덱스 | `_guides/GUIDES.md` | 문서 목록 및 상태 |
