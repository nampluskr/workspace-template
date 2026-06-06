# {프로젝트 제목}

{프로젝트에 대한 한 줄 설명}

> 생성일시: YYMMDD-HHMMSS
> 수정일시: YYMMDD-HHMMSS
> 주제: {Subject Name}

**목차**

1. [개요](#1-개요)
2. [주제 분류](#2-주제-분류)
3. [디렉토리 구조](#3-디렉토리-구조)

## 1. 개요

{프로젝트의 목적, 배경, 범위를 간략히 기술한다.}

## 2. 주제 분류

{적용되는 subject code (MATH, PHYS, NA, ML, CV, NLP, CS, DEV, MISC 등)와 세부 분류를 기술한다.}

분류 목록 및 세부 항목은 [_workspace/rules/subject-classification.md](_workspace/rules/subject-classification.md) 를 참조한다.

## 3. 디렉토리 구조

```text
project-root/
├── README.md               # 프로젝트 외부 소개 (이 파일)
├── PROJECT.md              # 프로젝트 내부 명세
├── TASKS.md                # Stage-Phase-Task 진행 관리
├── CLAUDE.md               # AI CLI 운영 지침
├── _workspace/             # 워크스페이스 운영 관리
├── _assets/                # 읽기 전용 입력 보관소
├── scripts/                # 실행 스크립트 및 Python 파일
├── outputs/                # 프로젝트 산출물
└── docs/                   # 최종 산출물 (Jupyter Book v2)
    ├── myst.yml
    └── contents/
        └── chapXX/
            └── images/
```
