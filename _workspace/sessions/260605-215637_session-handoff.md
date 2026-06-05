# 주제 분류 체계 반영 세션 핸드오프

> 작성일시: 260605-220755
> 세션 목적: Subject Classification을 워크스페이스 문서 체계에 반영
> 이전 핸드오프: 260605-213711_session-handoff.md

---

## 1. 세션 핵심 요약

- 사용자가 9개 subject code(MATH, PHYS, NA, ML, CV, NLP, CS, DEV, MISC) 분류 체계를 제시
- `_workspace/rules/subject-classification.md` 신규 생성
- `_workspace/docs/workspace-guide.md`에 "7. 주제 분류 체계" 섹션 추가
- `PROJECT.md`, `README.md` 태그 자리표시자에 `{subject-code}` 추가
- 섹션명 언어 정책 확정: H1·H2는 한국어, H3 주제명(subject name)은 영어 원문 유지
- 세부 항목은 체크리스트가 아닌 일반 목록으로 변경 (예시 성격 명시)
- 항목 중 한국어로 작성된 "pi 계산", "카오스와 프랙탈"을 영어로 수정

---

## 2. 사용자 요청 및 의도

| 요청 내용 | 배경 목적 |
| --- | --- |
| Subject Classification을 워크스페이스 문서에 반영 | 문서 작성, 파일명, 태그 결정 시 공통 기준으로 활용 |
| 섹션명 한국어 사용 | writing-style.md 규칙 적용 (제목/섹션명은 한국어 우선) |
| H3 주제명은 영어 유지 | subject code와 쌍을 이루는 고유명사로 취급 |
| 체크박스 제거, "예시" 명시 | 진행 상태 추적 목적이 아닌 분류 기준 참조 문서임을 명확히 |
| 한국어 항목을 영어로 수정 | 세부 항목도 영어로 통일 |

---

## 3. 확정된 결정사항

| 항목 | 확정 내용 | 비고 |
| --- | --- | --- |
| 규칙 파일 위치 | `_workspace/rules/subject-classification.md` | 신규 생성 완료 |
| H1 제목 | `# 주제 분류 체계` | 한국어 |
| H2 섹션명 | `## 2 분류 목록`, `## 3 분류별 세부 항목 예시` | 한국어 |
| H3 섹션명 | `### 3.1 [MATH] Mathematics` 형식 | subject code + 영어 subject name |
| 세부 항목 형식 | 체크박스 없는 일반 목록 | 예시 성격 |
| 태그 자리표시자 | `태그: {subject-code}, {tag1}, {tag2}` | PROJECT.md, README.md 공통 |
| workspace-guide.md | 섹션 7 추가, 목차 8번으로 확장 | 사용 시 주의사항은 8번으로 밀림 |

---

## 4. AI 핵심 제안 및 분석

- **subject code를 태그 첫 번째 위치에 배치**
  - 문서 분류 기준으로 가장 먼저 식별되어야 하는 값이므로 첫 번째 위치가 적합
  - 사용자 수용

- **`{subject-code}` 자리표시자를 템플릿에 삽입**
  - 실제 프로젝트에 템플릿 적용 시 subject code를 빠뜨리지 않도록 유도
  - PROJECT.md, README.md 모두 동일하게 적용

---

## 5. 미결 사항

미결 사항 없음.

---

## 6. 다음 작업 목록

| 우선순위 | 작업 | 관련 폴더/파일 | 사용할 도구 |
| --- | --- | --- | --- |
| 1 | TASKS.md에 이번 작업 내용 반영 여부 확인 | `TASKS.md` | Read, Edit |
| 2 | writing-style.md에 subject code 태그 사용 규칙 추가 (필요 시) | `_workspace/rules/writing-style.md` | Read, Edit |

---

## 7. 다음 세션에서 이어받기

### 새 세션 시작 지시문:

"아래는 이전 세션의 컨텍스트입니다.
이 내용을 기반으로 작업을 이어받아 주세요.

이번 세션에서 주제 분류 체계(`_workspace/rules/subject-classification.md`)가 신규 생성되었고,
`_workspace/docs/workspace-guide.md`에 관련 섹션이 추가되었습니다.
`PROJECT.md`와 `README.md`의 태그 자리표시자도 `{subject-code}`를 포함하도록 수정되었습니다.

다음 작업을 우선적으로 다뤄주세요:
1. `TASKS.md`에 이번 작업 내용이 반영되어야 할 항목이 있는지 확인하고 업데이트
2. `_workspace/rules/writing-style.md`에 subject code 태그 사용 규칙 추가 여부를 사용자와 논의"

---

## 8. 참고 자료 및 링크

| 항목 | 위치/경로 | 용도 |
| --- | --- | --- |
| 주제 분류 체계 | `_workspace/rules/subject-classification.md` | subject code 및 세부 항목 예시 |
| 워크스페이스 가이드 | `_workspace/docs/workspace-guide.md` | subject code 활용 방법 설명 |
| 문서 작성 스타일 | `_workspace/rules/writing-style.md` | 섹션명 언어 규칙 기준 |
| 프로젝트 명세 템플릿 | `PROJECT.md` | 태그 자리표시자 포함 |
| 외부 소개 템플릿 | `README.md` | 태그 자리표시자 포함 |
