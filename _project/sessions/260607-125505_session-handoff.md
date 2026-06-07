# 워크스페이스 템플릿 구조 개선 세션 핸드오프

> 작성일시: 260607-125505
> 세션 목적: §1 용어 정의 섹션 삭제 및 `_workspace` → `_project` 폴더명 변경
> 이전 핸드오프: 260607-123808_session-handoff.md

## 1. 세션 핵심 요약

- `_workspace`는 단일 프로젝트(GitHub 레포 단위) 전용이므로 "워크스페이스 vs 프로젝트" 구분이 불필요하다는 결론 도달
- CLAUDE.md §1 용어 정의 섹션 전체 삭제 — §1.1만 삭제하면 §1 도입부가 불완전해지므로 §1 전체 제거
- 기존 §2~§11을 §1~§10으로 재번호 부여, 본문 내 교차 참조(`§1`, `§4`, `§10.2`) 갱신
- `_workspace/` → `_project/` 폴더명 변경 — 폴더 내용(PROJECT.md, TASKS.md, commands/, rules/)이 프로젝트 관리 파일이므로 명칭 일치
- AGENTS.md를 CLAUDE.md와 동일 내용으로 동기화
- `_project/` 내부 파일(commands 6개, rules/markdown-style.md) `_workspace` → `_project` 일괄 치환
- `_assets/project-dashboard.md` 내 `_workspace` 참조 2개는 `_assets/` 수정 금지 규칙으로 인해 미처리 상태

## 2. 사용자 요청 및 의도

| 요청 내용 | 배경 목적 |
| --- | --- |
| CLAUDE.md §1.1 항목 필요성 검토 | `_workspace`가 단일 프로젝트 전용이 되면서 워크스페이스/프로젝트 구분 불필요 |
| `_workspace` → `_project` 폴더명 변경 검토 및 적용 | 폴더 내용이 프로젝트 관리 파일 중심이므로 명칭을 내용에 맞게 정렬 |

## 3. 확정된 결정사항

| 항목 | 확정 내용 | 비고 |
| --- | --- | --- |
| §1 용어 정의 삭제 범위 | §1.1만이 아닌 §1 전체(헤더+도입부+§1.1) 삭제 | 도입부가 §1.1에 의존하므로 §1 전체 제거 |
| 섹션 재번호 | §2~§11 → §1~§10 | CLAUDE.md, AGENTS.md 동일 적용 |
| 폴더 변경 | `_workspace/` → `_project/` | `_` 접두사(내부 운영 폴더 식별) 유지 |
| 세션 이력 파일 처리 | `_project/sessions/260*.md` 내 `_workspace` 참조 미변경 | 과거 시점 기록이므로 수정 불필요 |
| `_assets/` 내 파일 처리 | `_assets/project-dashboard.md` 내 참조 미변경 | `_assets/` 수정 금지 규칙 적용 |

## 4. AI 핵심 제안 및 분석

- **§1.1 단독 삭제 불가 판단**
  - §1 도입부가 "사용자는 두 용어를 혼용할 수 있으며..."로 §1.1을 전제하므로, §1.1만 삭제하면 §1이 불완전해짐
  - §1 전체 삭제가 올바른 처리임을 분석하여 제안, 사용자 수용

- **폴더명 `_project` 채택 근거**
  - `_workspace/` 내용: PROJECT.md, TASKS.md, commands/, rules/, sessions/
  - 모두 프로젝트 관리 파일이므로 `_project`가 내용을 더 정확히 표현
  - `_` 접두사는 "내부 운영/보조 폴더" 의미로 유지

## 5. 미결 사항

| # | 항목 | 현재 상태 | 결정 필요 내용 |
| --- | --- | --- | --- |
| 1 | `_assets/project-dashboard.md` 내 `_workspace` 참조 | 미처리 | `_assets/` 수정 금지 규칙 예외 적용 여부 또는 파일 이동 검토 |

## 6. 다음 작업 목록

| 우선순위 | 작업 | 관련 폴더/파일 | 비고 |
| --- | --- | --- | --- |
| 1 | `_assets/project-dashboard.md` 내 `_workspace` → `_project` 수정 여부 결정 | `_assets/project-dashboard.md` | 사용자 직접 수정 또는 파일을 `_project/docs/` 로 이동 검토 |
| 2 | CLAUDE.md 기준으로 실제 개별 프로젝트 레포에 적용 테스트 | 전체 구조 | 템플릿 완성도 확인 |

## 7. 다음 세션에서 이어받기

### 새 세션 시작 지시문:

```
session-start 실행 후 _assets/project-dashboard.md 내 _workspace 참조 처리 방향을 결정하고, 템플릿 완성도를 점검해 주세요.
```

## 8. 참고 자료 및 링크

| 항목 | 위치/경로 | 용도 |
| --- | --- | --- |
| AI CLI 운영 지침 | `CLAUDE.md` | §1~§10 구조, `_project/` 기반 |
| 프로젝트 운영 폴더 | `_project/` | commands/, rules/, sessions/ 포함 |
| 미처리 참조 파일 | `_assets/project-dashboard.md` | `_workspace` 참조 2개 잔존 |
