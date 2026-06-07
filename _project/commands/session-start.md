# 커스텀 명령어: `session-start` / `세션 시작`

새 작업 세션 시작 시 `session-start 실행` 또는 `@session-start.md 실행` 으로 호출한다.
프로젝트 현황과 직전 세션 미결 사항을 파악하여 세션 브리핑을 출력한다.

## 실행 절차

### Step 1. 컨텍스트 로딩

1. `_project/PROJECT.md` 를 읽어 프로젝트명, 목적, 진행 단계를 파악한다.
2. `_project/PROJECT-TODO.md` 를 읽어 현재 Stage/Phase 와 미완료 Task 목록을 파악한다.

### Step 2. 직전 세션 핸드오프 확인

1. `_project/sessions/` 에서 파일 목록을 확인한다.
2. 가장 최근 파일을 읽어 미결 사항과 다음 작업 목록을 파악한다.
3. 파일이 없으면 첫 번째 세션으로 처리한다.

### Step 3. 세션 브리핑 출력

아래 형식으로 브리핑을 출력한다.

```
== 세션 시작 브리핑 ==

프로젝트: {프로젝트명}
현재 단계: Stage {N} {Stage명} > Phase {N.M} {Phase명}

[ 이어서 할 작업 ]
- [ ] Task 1
- [ ] Task 2

[ 직전 세션 미결 사항 ]       ← 없으면 이 항목 생략
- ...

[ 참고 ]
직전 핸드오프: _project/sessions/{파일명}   ← 없으면 이 항목 생략
```
