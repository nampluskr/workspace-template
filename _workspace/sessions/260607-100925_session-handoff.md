# 워크스페이스 규칙 파일 정비 세션 핸드오프

> 작성일시: 260607-100925
> 세션 목적: writing-style.md 도입 문장 규칙 추가 및 coding-style 파일 언어별 분리
> 이전 핸드오프: `_workspace/sessions/260607-082829_session-handoff.md`

## 1. 세션 핵심 요약

- `writing-style.md` §2.7 도입 문장 규칙 신규 추가 — 테이블·목록 앞 1문장 이상 필수, "다음과 같다" 연결만 금지
- `writing-style.md` 및 `subject-classification.md` 전체에 도입 문장 소급 적용
- `coding-style.md` 삭제 → `coding-style-python.md` + `coding-style-notebook.md`로 분리
- `coding-style-python.md`에 `_assets/python-coding-style-summary.md` 내용(네이밍 규칙, 세로 정렬 금지, kwargs 금지, 타입 힌트, print 규칙) 통합
- `coding-style-notebook.md` 신규 작성 — Jupyter Book v2 문서 구조, 마크다운 셀 규칙, matplotlib 설정 포함
- `CLAUDE.md` / `AGENTS.md` §7 참조 경로를 언어별 파일로 업데이트

## 2. 사용자 요청 및 의도

| 요청 내용 | 배경 목적 |
| --- | --- |
| 도입 문장 지침을 문서에 추가 | 지침 파일에 규칙이 명시되어야 AI CLI가 일관되게 따를 수 있음 |
| "다음과 같다" 연결 표현 금지로 수정 | 내용 없는 연결 문장은 규칙의 취지에 어긋남 |
| coding-style 파일 분리 | Python과 Jupyter Notebook 규칙이 혼재, C++ 추가 예정으로 언어별 분리 필요 |
| `python-coding-style-summary.md` 내용 반영 | Claude.ai에서 자주 요청하는 지침을 워크스페이스 공식 파일에 통합 |
| Jupyter Notebook에 Jupyter Book v2 지침 추가 | 노트북이 최종 배포 문서로 빌드되므로 문서 구조·마크다운 셀 규칙 명시 필요 |

## 3. 확정된 결정사항

| 항목 | 확정 내용 | 비고 |
| --- | --- | --- |
| 도입 문장 기준 | 1문장 이상, 맥락·존재 이유를 포함, "다음과 같다"만으로는 불가 | writing-style.md §2.7, CLAUDE.md §2.3 |
| coding-style 파일 네이밍 | `coding-style-python.md` / `coding-style-notebook.md` | 언어별 접미사 방식 |
| C++ 확장 파일명 | `coding-style-cpp.md` (향후 생성) | |
| notebook Figure 설명 위치 | 코드 셀 다음 마크다운 셀 (Figure 출력 아래에 캡션 표시) | Jupyter Book v2 렌더링 기준 |
| AGENTS.md 동기화 | CLAUDE.md와 항상 동일 내용 유지 | 수동 동기화 방식 유지 |

## 4. AI 핵심 제안 및 분석

- **coding-style 파일 분리 네이밍 방식 제안**
  - `python-style.md` / `cpp-style.md` 방식과 `coding-style-python.md` / `coding-style-cpp.md` 방식 비교 제시
  - 사용자가 `coding-style-python.md` / `coding-style-notebook.md` 접미사 방식 선택

- **notebook-style 별도 파일 분리 제안**
  - Jupyter Notebook 지침이 문서 구조(writing-style.md 관련)와 코드(coding-style 관련)가 교차하는 독립 영역임을 근거로 분리 권장
  - 사용자 수용

## 5. 미결 사항

미결 사항 없음.

## 6. 다음 작업 목록

| 우선순위 | 작업 | 관련 폴더/파일 | 비고 |
| --- | --- | --- | --- |
| 1 | C++ 코딩 스타일 가이드 작성 | `_workspace/rules/coding-style-cpp.md` | 알고리즘, 자료구조, 코딩테스트, 실제 C++ 작업 대상 |
| 2 | 실제 프로젝트 시작 시 `project-init 실행`으로 PROJECT.md / TASKS.md 작성 | `PROJECT.md`, `TASKS.md` | 현재 TASKS.md는 템플릿 상태 |

## 7. 다음 세션에서 이어받기

### 새 세션 시작 지시문

```
session-start 실행 후 필요한 작업을 진행해 주세요.
```

## 8. 참고 자료 및 링크

| 항목 | 위치/경로 | 용도 |
| --- | --- | --- |
| 도입 문장 규칙 | `_workspace/rules/writing-style.md §2.7` | 테이블·목록 앞 도입 문장 기준 |
| Python 코딩 스타일 | `_workspace/rules/coding-style-python.md` | Python 전용 규칙 |
| Notebook 코딩 스타일 | `_workspace/rules/coding-style-notebook.md` | Jupyter Notebook + Jupyter Book v2 규칙 |
| Python 스타일 원본 요약 | `_assets/python-coding-style-summary.md` | coding-style-python.md에 통합 완료 |
