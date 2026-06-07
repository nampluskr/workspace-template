# CUDA + PyTorch 환경 구성 가이드 작성 세션 핸드오프

> 작성일시: 260607-162550
> 세션 목적: CUDA 버전 선택 근거 조사 및 cuda-pytorch-guide.md 작성
> 이전 핸드오프: 260607-151653_session-handoff.md

## 1. 세션 핵심 요약

- GTX 1080 Ti(Pascal, CC 6.1) 환경에서 CUDA 버전 선택 근거를 원점에서 재검토
- PyTorch 2.8부터 CUDA 12.8 빌드에서 Pascal 지원 제거 확인 — CUDA 12.6이 실용적 상한
- PyTorch 2.7 기준 공식 지원 CUDA: 11.8 / 12.6 / 12.8 세 가지 (12.4 제외됨)
- 레거시 코드 평가 목적으로 CUDA 11.8 메인, CUDA 12.1 추가 평가 방향 확정
- PyTorch 2.5.1이 CUDA 11.8과 12.1을 동시에 공식 지원하는 마지막 버전임 확인
- WinPython 3.11.8.0 dot 버전 선택 — 3.11 시리즈 slim 없음, dot(25.3MB)이 최소 구성
- cuda-guide.md 신규 생성 후 cuda-pytorch-guide.md로 rename
- GUIDES.md에 cuda-{framework}-guide.md 시리즈 4개 항목 등록
- PROJECT-TODO.md / PROJECT-HISTORY.md 템플릿 → 실제 내용으로 초기화

## 2. 사용자 요청 및 의도

| 요청 내용 | 배경 목적 |
|-----------|-----------|
| CUDA 버전 제안 및 비교 (PyTorch 컴퓨터 비전 메인) | 레거시 환경 평가 + 최신 환경 호환성 확인 |
| cuda-guide.md 문서 생성 | CUDA 환경 구축 절차 기록 |
| 11.8 메인, 12.x 추가 평가 방향 재검토 | 기존 레거시 환경 기준 코드 리팩토링 목적 |
| 12.1/12.2 중 안정적 버전 확인 | 가장 많이 검증된 12.x 버전 선택 |
| WinPython 신규 다운로드 버전 검토 | 기존 설치 환경의 불필요한 패키지 제거 |
| 4개 환경을 독립 섹션으로 작성 | 각 섹션만으로 설치 가능한 독립 완결 문서 |
| 문서 네이밍 제안 | TensorFlow / JAX / CuPy 추가 문서 시리즈 수립 |

## 3. 확정된 결정사항

| 항목 | 확정 내용 | 비고 |
|------|-----------|------|
| CUDA 버전 (메인) | 11.8 | 레거시 코드 평가 기준 |
| CUDA 버전 (추가) | 12.1 | PyTorch 2.5.1 공식 지원 마지막 12.x |
| PyTorch 버전 | 2.5.1 | CUDA 11.8 / 12.1 동시 지원 |
| torchvision | 0.20.1 | PyTorch 2.5.1 대응 버전 |
| Python 버전 | 3.11 | 2024~2025 ML 환경 최다 검증 버전 |
| WinPython | 3.11.8.0 dot (`Winpython64-3.11.8.0dot.exe`, 25.3MB) | 3.11 시리즈 slim 없음 |
| Windows 설치 경로 | `C:\winpython\WPy64-3118_cu118\`, `C:\winpython\WPy64-3118_cu121\` | 각 환경 별도 폴더 |
| WSL2 conda 환경명 | `pytorch_cu118`, `pytorch_cu121` | |
| 가이드 파일명 시리즈 | `cuda-{framework}-guide.md` 패턴 | cuda-pytorch/tensorflow/jax/cupy |

## 4. AI 핵심 제안 및 분석

- **CUDA 버전 선택 근거 정리**
  - PyTorch 2.7(최신 stable) 공식 지원: 11.8 / 12.6 / 12.8 (12.4는 2.7에서 제외)
  - CUDA 12.8 빌드: Pascal(CC 6.x) 지원 제거 → GTX 1080 Ti 사용 불가
  - CUDA 12.1이 12.x 범위에서 가장 안정적으로 검증된 버전 (PyTorch 2.1~2.6 지원)
  - CUDA 11.8 + 12.1을 동시 공식 지원하는 최신 버전 = PyTorch 2.5.1

- **WinPython 버전 분석**
  - 3.10: WinPython 신규 릴리즈 2023년 5월 중단
  - 3.11: 정식 최신 3.11.8.0 (2024-02), slim 없음, dot(최소 구성) 존재
  - 3.12: slim 존재(3.12.10.0), 그러나 C 확장 wheel 공급이 3.11보다 늦었음
  - 3.11이 ML 환경 기준 가장 넓게 검증된 버전으로 권장

- **파일명 시리즈 설계**
  - cuda- 접두사로 통일 → 파일 정렬 시 자동 그룹화
  - cuda-guide.md를 cuda-pytorch-guide.md로 rename하여 PyTorch 전용임을 명시

## 5. 미결 사항

| # | 항목 | 현재 상태 | 결정 필요 내용 |
|---|------|-----------|----------------|
| 1 | WinPython 3.12 버전 기존 환경 처리 | 기존 WPy64-312101 미사용 예정 | 삭제 여부 사용자 결정 필요 |
| 2 | cuda-tensorflow-guide.md | 미작성 | 다음 작업 |
| 3 | cuda-jax-guide.md | 미작성 | 다음 작업 |
| 4 | cuda-cupy-guide.md | 미작성 | 다음 작업 |
| 5 | conda-env-guide.md | 미작성 | 각 가상환경 용도·패키지 기록 |

## 6. 다음 작업 목록

| 우선순위 | 작업 | 관련 파일 | 비고 |
|----------|------|-----------|------|
| 1 | cuda-tensorflow-guide.md 작성 | `_guides/docs/cuda-tensorflow-guide.md` | 동일 4환경 구조, TF 버전 호환성 조사 필요 |
| 2 | cuda-jax-guide.md 작성 | `_guides/docs/cuda-jax-guide.md` | JAX + jaxlib CUDA 버전 매핑 조사 필요 |
| 3 | cuda-cupy-guide.md 작성 | `_guides/docs/cuda-cupy-guide.md` | CuPy CUDA 버전별 패키지명 확인 필요 |
| 4 | conda-env-guide.md 작성 | `_guides/docs/conda-env-guide.md` | 각 가상환경 용도·패키지 목록 |
| 5 | env-spec.md §1.3 갱신 | `_guides/docs/env-spec.md` | WinPython 버전 변경 반영 |

## 7. 다음 세션에서 이어받기

### 새 세션 시작 지시문

"session-start 실행 후 cuda-tensorflow-guide.md 작성을 진행해 주세요.

GTX 1080 Ti(Pascal, CC 6.1) 환경 기준으로, CUDA 11.8 / 12.1 각각에서
TensorFlow 버전 호환성을 먼저 확인하고, cuda-pytorch-guide.md와 동일한
4개 독립 섹션 구조(환경 1~4)로 작성합니다.
Windows는 WinPython 3.11.8.0 dot + pip, WSL2는 Anaconda conda 환경 기준입니다."

## 8. 참고 자료 및 링크

| 항목 | 위치/경로 | 용도 |
|------|-----------|------|
| CUDA + PyTorch 가이드 | `_guides/docs/cuda-pytorch-guide.md` | 4개 환경 구축 절차 |
| 개발 환경 명세 | `_guides/docs/env-spec.md` | 하드웨어·OS 기준 문서 |
| 가이드 인덱스 | `_guides/GUIDES.md` | 문서 목록 및 상태 |
| PyTorch 이전 버전 | https://pytorch.org/get-started/previous-versions/ | 2.5.1 설치 명령 참조 |
| WinPython 3.11.8.0 | https://sourceforge.net/projects/winpython/files/WinPython_3.11/3.11.8.0/ | dot 버전 다운로드 |
| Pascal 지원 제거 공지 | https://dev-discuss.pytorch.org/t/cuda-toolkit-version-and-architecture-support-update-maxwell-and-pascal-architecture-support-removed-in-cuda-12-8-and-12-9-builds/3128 | CUDA 12.8 Pascal 제거 근거 |
