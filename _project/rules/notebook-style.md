# Notebook 스타일 가이드

Jupyter Book v2 배포를 목표로 하는 노트북 작성에 적용되는 문서 구조 및 코드 규칙이다.
노트북 내 Python 코드 작성 규칙은 `coding-style-python.md`를 따른다.

> 생성일시: 260607-140000
> 수정일시: 260607-150000
> 주제: Development Environment and Tools

**목차**

1. [문서 구조](#1-문서-구조)
2. [마크다운 셀 작성 규칙](#2-마크다운-셀-작성-규칙)
3. [matplotlib 설정](#3-matplotlib-설정)
4. [Figure 저장](#4-figure-저장)

## 1. 문서 구조

### 1.1. 콘텐츠 노트북 셀 구성

Jupyter Book v2 페이지로 빌드되는 콘텐츠 노트북은 마크다운과 코드 셀을 아래 원칙에 따라 구성한다.

- 첫 번째 셀은 마크다운 셀로 작성하며 H1 제목, 요약(1~2줄), 메타 블럭을 포함한다.
- 헤더 계층과 섹션 번호는 `writing-style.md §5`를 따른다.
- 목차는 `writing-style.md §2.4` 형식을 따르며 페이지 분량이 많은 경우에 삽입한다.
- Jupyter Book v2 렌더링 관련 추가 규칙은 `writing-style.md §9`를 따른다.

### 1.2. Figure 생성 노트북 셀 구성

Figure만 생성하는 전용 노트북은 출력 제어 셀을 앞에 두고 Figure 단위로 반복하는 구조로 작성한다.

1. Markdown 셀: 노트북 제목 및 경로
2. Code 셀: `rcParams` 설정 (태그: `remove-cell`)
3. Code 셀: output 설정 (태그: `remove-cell`)
4. Code 셀: 공유 스타일 변수 정의
5. 반복: Code 셀(Figure 코드) + Markdown 셀(Figure 번호/캡션/설명)

### 1.3. 메타 블럭

콘텐츠 노트북의 첫 번째 마크다운 셀에는 `writing-style.md §2.2`에 따라 메타 블럭을 포함한다.

```markdown
# 노트북 제목

요약 1~2줄

> 생성일시: YYMMDD-HHMMSS
> 수정일시: YYMMDD-HHMMSS
> 주제: Subject Name
```

## 2. 마크다운 셀 작성 규칙

### 2.1. 텍스트 및 문체

마크다운 셀의 텍스트는 `writing-style.md §4`의 언어 및 문체 규칙을 따른다. 본문은 한국어 서술체로 작성하며, 수학·기술 용어는 영어 단독 표기를 원칙으로 한다.

- 문장 종결: `~한다`, `~이다` (경어체 `~합니다`, `~입니다` 금지)
- 튜토리얼/교육적 어조 금지 — 독자를 단계별로 안내하는 설명 방식은 사용하지 않는다

### 2.2. 수식

마크다운 셀의 수식은 `writing-style.md §6`의 수식 작성 규칙을 따른다. Inline 수식은 `$...$`, Display 수식은 `$$...$$` 형식을 사용하며, LaTeX 표기는 `writing-style.md §6.3` 통일 기준을 따른다.

### 2.3. Figure 마크다운 셀

matplotlib으로 생성한 Figure의 설명은 Figure 코드 셀 다음 마크다운 셀에 작성한다. 이 순서는 Jupyter Book v2 렌더링 시 Figure 출력 아래에 캡션이 위치하도록 보장한다.

```markdown
<!-- 코드 셀: Figure 생성 코드 -->

<!-- 다음 마크다운 셀 -->
**Figure N. 캡션 제목**

캡션에 대한 상세 설명을 별도 paragraph로 작성한다.
```

캡션과 상세 설명의 세부 작성 규칙은 `writing-style.md §7.2`를 따른다.

### 2.4. admonition 블록

참고 및 주의 사항은 MyST admonition 블록으로 표기한다. 일반 텍스트나 볼드 강조 대신 아래 지시어를 사용하여 독자에게 시각적으로 구분되는 보조 정보를 제공한다.

```markdown
```{note}
Weierstrass M-test: 수렴 조건을 서술한다.
```

```{warning}
Uniform Limit Theorem 적용 조건: 주의할 사항을 서술한다.
```
```

자주 사용하는 admonition 지시어와 용도는 다음과 같다.

| 지시어 | 용도 |
|---|---|
| `{note}` | 부연 설명, 정의 보충, 참고 사항 |
| `{warning}` | 오류 발생 조건, 적용 제한, 주의 사항 |
| `{tip}` | 관련 기법, 효율적 접근 방법 |
| `{important}` | 핵심 조건, 반드시 지켜야 할 사항 |

## 3. matplotlib 설정

### 3.1. rcParams 설정

DPI는 `rcParams` 내 `savefig.dpi`로 설정하며 별도 변수로 분리하지 않는다.

```python
import matplotlib as mpl

mpl.rcParams.update({
    "figure.dpi": 100,
    "savefig.dpi": 150,
    "font.size": 11,
    "axes.linewidth": 0.8,
})
```

### 3.2. 공유 스타일 변수

스타일 변수는 `rcParams` 셀 이후 별도 셀에서 정의한다.

```python
# Shared style variables for all figures
FS_LABEL = 12  # axis label font size
FS_TICK = 10  # tick label font size
LW_CURVE = 1.8  # curve line width
MS_ARROW = 12  # arrow marker size
C_MAIN = "#2c7bb6"  # main curve color
C_FILL = "#d7ecf7"  # fill color
```

### 3.3. 레이블 언어

matplotlib의 모든 레이블(축 이름, 범례, 제목)은 영어 또는 LaTeX 전용으로 작성한다. 한국어 텍스트는 matplotlib에서 사용하지 않는다.

## 4. Figure 저장

### 4.1. 저장 경로

Figure 저장 경로는 `os.path` 방식을 사용하며, 파일명은 `writing-style.md §7.1` 형식(`fig-{lecture_id}-{figure_id}.png`)을 따른다.

```python
import os

output_dir = os.path.join("images")
os.makedirs(output_dir, exist_ok=True)
fig.savefig(os.path.join(output_dir, "fig-001-001.png"), bbox_inches="tight")
```
