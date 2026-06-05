# 연구/학습 워크스페이스

수학, 물리, 수치해석, 머신러닝, 컴퓨터비전, 자연어처리 등 연구 및 학습 자료를 정리하는 워크스페이스

> 생성일: 2026-06-05
> 수정일: 2026-06-05
> 주제: {Subject Name}

---

**목차**

1. [개요](#1-개요)
2. [주제 분류](#2-주제-분류)
3. [디렉토리 구조](#3-디렉토리-구조)

---

## 1 개요

이 워크스페이스는 수학, 물리, 수치해석, 머신러닝, 컴퓨터 비전, 자연어처리, 컴퓨터과학 분야의 연구 및 학습 자료를 체계적으로 정리하고 Jupyter Book 형태의 문서로 산출하기 위한 환경이다.

- AI CLI(Claude, Codex 등)와 협업하여 자료를 작성하고 관리한다.
- `_workspace/` 폴더에 운영 규칙, 세션 기록, 커스텀 명령어를 보관한다.
- 최종 산출물은 `docs/` 에 Jupyter Book v2 형태로 빌드된다.

---

## 2 주제 분류

MATH, PHYS, NA, ML, CV, NLP, CS, DEV, MISC 의 subject code 를 기준으로 분류한다.

분류 목록 및 세부 항목은 [_workspace/rules/subject-classification.md](_workspace/rules/subject-classification.md) 를 참조한다.

---

## 3 디렉토리 구조

```text
project-root/
├── README.md               # 프로젝트 외부 소개 (이 파일)
├── PROJECT.md              # 프로젝트 내부 명세
├── TASKS.md                # Stage-Phase-Task 진행 관리
├── CLAUDE.md               # AI CLI 워크스페이스 운영 지침
├── _workspace/             # 워크스페이스 운영 관리
│   ├── commands/           # 커스텀 명령어 프롬프트
│   ├── docs/               # 워크스페이스 사용법 및 운영 문서
│   ├── rules/              # 워크스페이스 공통 규칙
│   └── sessions/           # 세션 핸드오프 문서
├── _assets/                # 읽기 전용 입력 보관소
├── scripts/                # 실행 스크립트 및 Python 파일
├── outputs/                # 프로젝트 산출물
└── docs/                   # 최종 산출물 (Jupyter Book v2)
    ├── myst.yml
    └── contents/
        └── chapXX/
            └── images/
```
