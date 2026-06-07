# [_guides 체계 구축] 세션 핸드오프

> 작성일시: 260607-135501
> 세션 목적: 워크스페이스 공통 도구 사용가이드 문서 체계(`_guides/`) 신설 및 첫 문서 작성
> 이전 핸드오프: 260607-130953_session-handoff.md

## 1. 세션 핵심 요약

이번 세션에서 논의되고 수행된 모든 항목이다.

- 기초/필수 도구 사용가이드 문서 체계 구성 방향 논의 — 문서 목록, 저장 위치, 폴더명 결정
- `_guides/` 폴더를 워크스페이스 루트에 신설 — `_project/`와 분리하여 프로젝트 교체와 무관하게 유지
- 폴더명 `_guides` vs `_refs` 비교 검토 후 `_guides` 채택 — 절차 중심 문서에 적합
- 파일명 접미사 `-guide` 결정 (예: `git-guide.md`)
- 개별 문서는 `_guides/docs/` 하위 폴더에 저장, 인덱스는 `_guides/GUIDES.md`에 관리
- `_guides/GUIDES.md` 인덱스 파일 생성 — 7개 가이드 문서 목록 및 상태 관리
- `git-guide.md` 작성 — 초보자 대상 시나리오별 Git 명령어 가이드 (전면 재작성 포함)
- `env-spec.md` 작성 — 하드웨어·OS·개발환경 버전 정보 기록용 템플릿
- CLAUDE.md / AGENTS.md 업데이트 — `_guides/` 폴더 규칙 반영, `PROJECT-HISTORY.md` 참조 문구 추가
- CLAUDE.md §2.3 신설 — 날짜·시각 처리 규칙 (실제 명령 확인 의무화)
- 메타정보 블록 형식 오류 수정 — `YYMMDD-HHMMSS` 형식 미준수 항목 일괄 교정

## 2. 사용자 요청 및 의도

이번 세션에서 사용자가 요청한 내용과 배경 목적이다.

| 요청 내용 | 배경 목적 |
|-----------|-----------|
| 기초/필수 도구 사용가이드 문서 목록과 저장 위치 제안 | 수시 참고 가능한 가이드 체계 구축 |
| `_project/docs/guides/` 저장 검토 | 프로젝트 문서와 공통 가이드 혼재 방지 |
| `_guides` vs `_refs` 네이밍 비교 | 폴더 의미에 맞는 이름 선택 |
| 파일명에 `-guide` 접미사 부여 | 파일 목적 명시화 |
| 개별 문서를 하위 폴더에 저장 | 인덱스와 본문 문서 분리 |
| `git-guide.md` 작성 (초보자, 시나리오별) | 실무 작업 흐름에 맞는 참고 문서 |
| git-guide.md 구조 개선 요청 (시나리오 → 서브섹션, 신규 토픽 추가) | 실제 사용 시나리오 확장 |
| `env-spec.md` 저장 위치 및 파일명 제안 | 환경 설정 가이드 작성 시 참조 기준 마련 |
| `env-spec.md` 템플릿 작성 | 사용자가 직접 값을 채워 넣는 방식 |
| `PROJECT-HISTORY.md` 참조 문구 추가 | AI CLI가 완료 이력을 참조할 수 있도록 |
| 날짜·시각 처리 규칙 CLAUDE.md에 명시 | 다른 세션에서도 동일하게 적용되도록 |

## 3. 확정된 결정사항

이번 세션에서 사용자가 명시적으로 확정한 내용이다.

| 항목 | 확정 내용 | 비고 |
|------|-----------|------|
| 가이드 폴더명 | `_guides/` — 워크스페이스 루트에 신설 | `_project/`와 분리 |
| 폴더명 선택 | `_guides` (절차 중심) | `_refs` 대비 내용 성격에 부합 |
| 파일명 형식 | `{주제}-guide.md` (접미사 방식) | 예: `git-guide.md` |
| 구조 | `_guides/GUIDES.md` (인덱스) + `_guides/docs/` (본문) | 하위 폴더 구조 |
| 환경 명세 파일 위치 | `_guides/docs/env-spec.md` | 절차 문서와 동일 위치 |
| 날짜·시각 처리 | `date +"%y%m%d-%H%M%S"` 명령 실행 후 실제 값 사용 — CLAUDE.md §2.3에 명시 | 임의 값 사용 금지 |

## 4. AI 핵심 제안 및 분석

- **`_guides/` 루트 신설 (vs `_project/docs/guides/`)**
  - `_project/`는 프로젝트별 교체 영역이므로 공통 가이드를 두면 프로젝트 교체 시 소실 위험
  - 루트에 `_guides/`로 분리하여 워크스페이스 수명 내내 유지
  - 사용자 수용

- **`env-spec.md`를 `_guides/` 루트가 아닌 `_guides/docs/`에 배치**
  - 성격상 참조 명세이나 사용자가 다른 가이드와 같은 위치 선호
  - 사용자 결정 존중하여 `docs/` 하위에 배치

## 5. 미결 사항

현재 미결 사항은 없다. 나머지 6개 가이드 문서는 필요 시 하나씩 작성 예정이다.

## 6. 다음 작업 목록

앞으로 필요에 따라 작성할 가이드 문서 목록이다.

| 우선순위 | 작업 | 관련 파일 |
|----------|------|-----------|
| 1 | `env-spec.md` 값 채워 넣기 — 사용자가 직접 수행 | `_guides/docs/env-spec.md` |
| 2 | `wsl-setup-guide.md` 작성 | `_guides/docs/wsl-setup-guide.md` |
| 3 | `conda-env-guide.md` 작성 | `_guides/docs/conda-env-guide.md` |
| 4 | `pytorch-gpu-guide.md` 작성 | `_guides/docs/pytorch-gpu-guide.md` |
| 5 | `jupyter-book-v2-guide.md` 작성 | `_guides/docs/jupyter-book-v2-guide.md` |
| 6 | `claude-code-guide.md` 작성 | `_guides/docs/claude-code-guide.md` |
| 7 | `vscode-guide.md` 작성 | `_guides/docs/vscode-guide.md` |

## 7. 다음 세션에서 이어받기

### 새 세션 시작 지시문:

"session-start 실행 후, `_guides/docs/` 에서 작성이 필요한 가이드 문서를 하나씩 작성해 주세요.
우선순위는 `wsl-setup-guide.md` → `conda-env-guide.md` → `pytorch-gpu-guide.md` 순입니다.
작성 전에 `_guides/docs/env-spec.md` 에 사용자가 채워 넣은 하드웨어·환경 정보를 먼저 확인하세요."

## 8. 참고 자료 및 링크

이번 세션에서 생성하거나 수정한 파일 목록이다.

| 항목 | 위치/경로 | 용도 |
|------|-----------|------|
| 가이드 인덱스 | `_guides/GUIDES.md` | 전체 가이드 문서 목록 및 상태 관리 |
| Git 가이드 | `_guides/docs/git-guide.md` | Git / GitHub 사용법 (완료) |
| 환경 명세 템플릿 | `_guides/docs/env-spec.md` | 하드웨어·OS·개발환경 버전 기록용 |
| 워크스페이스 운영 지침 | `CLAUDE.md` | `_guides/` 규칙, PROJECT-HISTORY.md 참조, §2.3 날짜 규칙 추가 |
| AI CLI 운영 지침 (Codex) | `AGENTS.md` | CLAUDE.md와 동일 내용 동기화 |
