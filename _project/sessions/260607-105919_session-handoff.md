# 워크스페이스 규칙 파일 정비 세션 핸드오프

> 작성일시: 260607-105919
> 세션 목적: coding-style 규칙 보완, subjects.md §3 개편, 파일명 변경, legacy/ 폴더 추가
> 이전 핸드오프: 260607-100925_session-handoff.md

## 1. 세션 핵심 요약

- `coding-style-notebook.md` 에 admonition 블록 규칙(§2.4) 신규 추가, §2.1에 튜토리얼/교육적 어조 금지 추가
- `coding-style-python.md` §3.1 한국어 금지 범위를 주석에서 docstring·type hint 까지 확장
- `subjects.md` §3 섹션명을 "분류별 세부 항목 예시" → "주제별 세부 내용" 으로 변경, §3.1~§3.9 각 주제별 Overview 문단 추가 (불릿 항목은 그대로 유지)
- `subject-classification.md` → `subjects.md` 로 파일명 변경, 활성 문서 내 참조 5곳 일괄 수정
- `legacy/` 폴더 신규 추가 (`_legacy/` 로 시작했다가 `_` 제거로 결정)
- CLAUDE.md §4.1 디렉토리 구조 그룹 구분선 추가, `_assets/` 주석 "바이너리" 보완

## 2. 사용자 요청 및 의도

| 요청 내용 | 배경 목적 |
| --- | --- |
| admonition 블록·레이블 언어 등 규칙을 지침 파일에 반영 | 노트북 작성 중 누락된 규칙을 지침 파일에 소급 명시 |
| subjects.md §3 를 Overview 문단 형식으로 재작성 | 불릿 나열에서 주제 소개 문단으로 — TOC가 아닌 Introduction 성격 |
| `subject-classification.md` → 간결한 파일명으로 변경 | "classification" 이 너무 길어 `subjects.md` 로 단축 |
| `legacy/` 폴더 추가 | 이전 문서·코드를 보관하여 현행 작업의 참고·보완 자료로 활용 |

## 3. 확정된 결정사항

| 항목 | 확정 내용 | 비고 |
| --- | --- | --- |
| subjects.md §3 형식 | 불릿 유지 + 섹션 헤더와 불릿 사이에 소주제 묶음별 Overview 문단 추가 | TOC식 나열 아님 |
| 파일명 | `subject-classification.md` → `subjects.md` | 가장 짧은 후보 채택 |
| `legacy/` 접두사 | `_` 없음 — 작업 소스 자료이므로 Git 추적 대상 | `_assets/` 는 바이너리·읽기전용이라 구분 |
| `_assets/` 주석 보완 | "바이너리 읽기 전용 입력 보관소" 로 명시 | 왜 Git에 올리지 않는지 이유 명시 |
| 한국어 코드 금지 범위 | 주석만 → 주석·docstring·type hint 모두 금지 | AI CLI는 항상 영어, 사용자 본인만 예외 |
| admonition 위치 | `coding-style-notebook.md §2.4` 신규 추가 | `{note}`, `{warning}`, `{tip}`, `{important}` 4종 |

## 4. AI 핵심 제안 및 분석

- **이미 반영된 항목 식별**
  - 사용자가 공유한 규칙 항목 중 레이블 언어, 테이블 기준, 이미지 경로, 실행 가능한 명령어, 서술체/경어체는 기존 파일에 이미 반영되어 있음을 확인하고 중복 추가 없이 진행

- **`_legacy` vs `legacy` 네이밍**
  - CLAUDE.md §5.1 접두사 규칙(`_` = 운영 보조, 없음 = 산출물/표준)을 기준으로 판단
  - 레거시 폴더는 작업 소스 자료(수정·가공 허용, Git 추적)이므로 `legacy/` 가 적합하다고 제안하여 채택

## 5. 미결 사항

| # | 항목 | 현재 상태 | 결정 필요 내용 |
| --- | --- | --- | --- |
| 1 | `_assets/` gitignore 처리 | 사용자가 이번 세션 보류 결정 | 별도 세션에서 `.gitignore` 생성 및 `_assets/` 등록 여부 결정 |

## 6. 다음 작업 목록

| 우선순위 | 작업 | 관련 파일 |
| --- | --- | --- |
| 1 | `.gitignore` 생성 및 `_assets/` 등록 (사용자 결정 시) | `.gitignore` 신규 생성 |
| 2 | `legacy/` 에 실제 레거시 파일 배치 | `legacy/` |
| 3 | `coding-style-cpp.md` 추가 (C++ 작업 시) | `_workspace/rules/` |

## 7. 다음 세션에서 이어받기

### 새 세션 시작 지시문:

"session-start 실행 후 다음 작업을 이어서 진행해 주세요.

우선 확인 사항:
1. `_assets/` 를 `.gitignore` 에 등록할지 여부 결정
2. `legacy/` 폴더에 보관할 파일이 있으면 이동 작업 진행"

## 8. 참고 자료 및 링크

| 항목 | 위치/경로 | 용도 |
| --- | --- | --- |
| coding-style-notebook.md | `_workspace/rules/coding-style-notebook.md` | admonition 블록(§2.4), 문체(§2.1) 규칙 |
| coding-style-python.md | `_workspace/rules/coding-style-python.md` | 한국어 금지 범위(§3.1) |
| subjects.md | `_workspace/rules/subjects.md` | 주제 분류 체계, §3 Overview 문단 포함 |
