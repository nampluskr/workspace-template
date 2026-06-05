# 문서 작성 스타일 가이드

워크스페이스 내 모든 기술/학술 문서에 적용되는 통합 작성 규칙 및 형식 지침이다.

> 생성일시: 260605-195326
> 수정일시: 260606-074638
> 주제: Development Environment and Tools

---

**목차**

1. [개요](#1-개요)
2. [문서 구조](#2-문서-구조)
3. [파일 및 폴더 규칙](#3-파일-및-폴더-규칙)
4. [언어 및 문체](#4-언어-및-문체)
5. [헤더 계층](#5-헤더-계층)
6. [수식 작성](#6-수식-작성)
7. [이미지 및 Figure](#7-이미지-및-figure)
8. [테이블](#8-테이블)
9. [Jupyter Book (MyST) 규칙](#9-jupyter-book-myst-규칙)
10. [참고문헌](#10-참고문헌)

---

## 1. 개요

### 1.1. 목적

이 문서는 워크스페이스 내에서 작성되는 모든 기술/학술 문서의 형식과 작성 규칙을 정의한다. AI 에이전트(Claude Code 등)가 문서를 생성하거나 편집할 때 이 가이드를 우선 참조한다.

### 1.2. 적용 범위

이 가이드는 아래 문서 유형에 공통 적용된다.

- 기술 문서: 개발 환경 설정, 워크플로우 가이드, API 레퍼런스
- 학술 노트: 수학/딥러닝 강의 노트, 논문 요약, 알고리즘 설명
- 지침 파일: CLAUDE.md, AGENTS.md, PROMPT.md, context/ 내 모든 파일

### 1.3. 출력 형식

이 가이드는 아래 출력 형식을 대상으로 한다.

- 일반 Markdown (.md)
- Jupyter Book / MyST Markdown
- LaTeX / PDF

출력 형식에 따른 특이사항은 해당 섹션에서 별도로 기술한다.

---

## 2. 문서 구조

### 2.1. 전체 구조 템플릿

모든 문서는 아래 순서를 따른다.

```markdown
# 제목

1줄~2줄 요약

> 생성일시: YYMMDD-HHMMSS
> 수정일시: YYMMDD-HHMMSS
> 주제: Subject Name

---

**목차**

1. [섹션 제목](#anchor)
2. [섹션 제목](#anchor)

---

## 1. 섹션 제목
### 1.1. 서브섹션 제목
#### 세부항목 제목

...

## N. 참고문헌
```

### 2.2. 메타정보 블록

메타정보는 제목 바로 아래, 목차 위에 blockquote (`>`) 형식으로 작성한다.

```markdown
> 생성일시: YYMMDD-HHMMSS
> 수정일시: YYMMDD-HHMMSS
> 주제: Subject Name
```

각 항목의 규칙은 다음과 같다.

- `생성일시`: 문서 최초 작성일시이며 이후 변경하지 않는다
- `수정일시`: 내용 변경 시마다 갱신한다
- `주제`: `_workspace/rules/subject-classification.md` 의 Subject 전체명을 사용한다. 복수 주제는 쉼표로 구분한다

### 2.3. 요약

- 제목 바로 아래, 메타정보 블록 위에 위치한다.
- 1줄~2줄 plain text로 작성하며 별도 레이블(`**요약:**` 등)을 붙이지 않는다.

### 2.4. 목차

- 구분선(`---`) 다음에 `**목차**` 굵은 글씨 레이블로 시작한다.
- 섹션은 번호 목록 + 바로가기 링크로 작성한다.
- 서브섹션과 H4 세부항목은 목차에 포함하지 않는다.

```markdown
**목차**

1. [섹션 제목](#anchor)
2. [섹션 제목](#anchor)
3. [섹션 제목](#anchor)
```

### 2.5. 참고문헌 섹션

참고문헌은 문서의 마지막 섹션으로 배치한다. 논문의 References에 해당하며 본문에서 인용한 모든 출처를 나열한다. 참고문헌이 없는 문서는 섹션 자체를 생략할 수 있다.

### 2.6. 불릿 분리 규칙

하나의 문단에 서로 독립적인 항목이 여러 개 포함된 경우 불릿 목록으로 분리한다.

- 분리 기준: 문장들이 서로 다른 규칙이나 항목을 나타낼 때
- 유지 기준: 문장들이 하나의 개념을 순차적으로 설명하거나 원인-결과 관계일 때

```markdown
# 분리 필요 (서로 다른 항목)
- 제목 바로 아래, 메타정보 블록 위에 위치한다.
- 1줄~2줄 plain text로 작성한다.

# 유지 (하나의 개념을 연속 서술)
참고문헌은 문서의 마지막 섹션으로 배치한다. 논문의 References에 해당하며
본문에서 인용한 모든 출처를 나열한다.
```

---

## 3. 파일 및 폴더 규칙

### 3.1. 파일명 규칙

파일명은 단어 구분에 하이픈(`-`)을 사용하고, 접두사와 접미사의 연결에는 언더스코어(`_`)를 사용한다.

```
# 올바른 예
lec-001_notes.md
fig-001-001.png
git-01_setup-windows.md

# 잘못된 예
lec001notes.md
Fig001_001.PNG
```

### 3.2. 날짜 형식

메타정보의 일시는 `YYMMDD-HHMMSS` 형식을 사용한다. 파일명에 날짜만 포함하는 경우 `YYMMDD` 형식을 사용한다.

```
260606-074638          ← 메타정보 일시
260606_meeting-summary.md   ← 파일명 날짜
```

### 3.3. 폴더 계층

폴더명은 3자리 숫자 접두사, 하이픈, 소문자 영어 순서로 구성한다.

```
010_inbox/
020_notes/
400_resources/
```

---

## 4. 언어 및 문체

### 4.1. 본문 언어

본문은 한국어로 작성한다. 명령어, 코드, 경로, 수식은 예외이며 영어 또는 LaTeX를 사용한다.

### 4.2. 수학/기술 용어 표기

수학 및 기술 용어는 영어 단독 표기를 원칙으로 한다. 처음 등장하는 용어라도 한국어(영어) 병기는 사용하지 않는다.

```
# 올바른 예
integral test, triangle inequality, absolutely convergent
batch normalization, learning rate, activation function

# 잘못된 예
적분 판정법(integral test)
삼각 부등식(triangle inequality)
배치 정규화(batch normalization)
```

### 4.3. 문체

문체 규칙은 `CLAUDE.md` / `AGENTS.md` §9 문서 작성 규칙에 정의되어 있다. 요약하면 다음과 같다.

- 본문은 서술체(`~이다`, `~한다`)를 사용한다.
- 경어체(`~입니다`, `~합니다`), 이모지, 불필요한 강조(볼드, 이탤릭)의 남용은 금지한다.
- 상세한 기술 문서 또는 전문적인 학술 문서 형식으로 작성한다.

---

## 5. 헤더 계층

### 5.1. 헤더 레벨 정의

| 레벨 | Markdown | 용도 | 번호 형식 |
|---|---|---|---|
| H1 | `#` | 문서 제목 | 없음 |
| H2 | `##` | 섹션 | `1.`, `2.`, `3.` |
| H3 | `###` | 서브섹션 | `1.1.`, `1.2.` |
| H4 | `####` | 세부항목 | 없음 |

### 5.2. 번호 표기 규칙

H2와 H3에는 번호를 붙인다. 번호 뒤에 점(`.`)을 붙이며 번호와 제목 사이는 공백 1칸으로 구분한다 (LaTeX/ACM/Springer 계열 관용). H4부터는 번호를 붙이지 않는다. Stage, Phase 번호에는 점을 붙이지 않는다.

```markdown
## 1. 개요
### 1.1. 목적
### 1.2. 범위
## 2. 설치
### 2.1. 사전 조건
#### 세부항목
```

### 5.3. 금지 사항

아래 사항은 금지한다.

- 헤더 레벨 건너뜀 (H2 다음 H4 직접 사용 불가)
- H4 이하 깊이 사용 (`#####` 등)
- 목차 레이블(`**목차**`)에 번호 부여

---

## 6. 수식 작성

### 6.1. Inline 수식

Inline 수식은 `$...$` 형식을 사용하며 `\(...\)` 형식은 사용하지 않는다. 수식은 반드시 한 줄에 작성하며 `$...$` 내부에서 줄바꿈을 허용하지 않는다.

```markdown
# 올바른 예
함수 $f(x) = x^2$ 는 실수 전체에서 연속이다.
$|\zeta(\sigma + it)| \leq \zeta(\sigma)$ 가 성립함을 보인다.

# 잘못된 예
함수 \(f(x) = x^2\) 는 연속이다.
$|\zeta(\sigma + it)| \leq
\zeta(\sigma)$ 가 성립함을 보인다.
```

### 6.2. Display 수식

Display 수식은 `$$...$$` 형식을 사용한다. 여러 줄 수식은 `aligned` 환경을 사용한다.

```markdown
$$
\zeta(s) = \sum_{n=1}^{\infty} \frac{1}{n^s}, \quad \operatorname{Re}(s) > 1
$$

$$
\begin{aligned}
f(x) &= ax^2 + bx + c \\
f'(x) &= 2ax + b
\end{aligned}
$$
```

### 6.3. LaTeX 표기 통일

| 항목 | 사용 | 금지 |
|---|---|---|
| 실수부 | `\operatorname{Re}(s)` | `\text{Re}(s)`, `Re(s)` |
| 허수부 | `\operatorname{Im}(s)` | `\text{Im}(s)` |
| 자연로그 | `\log` | `\ln` (밑 명시 시 `\log_e` 사용) |
| 절댓값 | `\lvert x \rvert` | `|x|` |
| 노름 | `\lVert x \rVert` | `||x||` |

### 6.4. 알고리즘 블록

일반 Markdown 문서에서 알고리즘은 번호 목록과 수식을 혼합하여 작성한다.

```markdown
**Algorithm 1. Gradient Descent**

Input: initial parameter $\theta_0$, learning rate $\eta$, iterations $T$
Output: optimized parameter $\theta^*$

1. Initialize $\theta \leftarrow \theta_0$
2. For $t = 1, \ldots, T$:
   1. Compute gradient $g \leftarrow \nabla_\theta \mathcal{L}(\theta)$
   2. Update $\theta \leftarrow \theta - \eta \cdot g$
3. Return $\theta$
```

---

## 7. 이미지 및 Figure

### 7.1. 파일명 규칙

Figure 파일명은 `fig-{lecture_id}-{figure_id}.png` 형식을 따른다.

```
fig-001-001.png   # lecture 1, figure 1
fig-002-003.png   # lecture 2, figure 3
```

### 7.2. 삽입 형식

이미지는 alt text, 굵은 글씨 캡션, 상세 설명 순서로 작성한다.

```markdown
![alt text](images/fig-001-001.png)
**Figure 1. 캡션 제목**

캡션에 대한 상세 설명을 별도 paragraph로 작성한다.
```

- alt text는 이미지 내용을 영어로 간략히 기술한다.
- 캡션은 이미지 바로 다음 줄에 굵은 글씨로 작성한다.
- 상세 설명은 캡션 다음 줄에 별도 paragraph로 작성한다.

### 7.3. Figure 번호

Figure 번호는 문서 내 sequential integer를 사용한다(`Figure 1.`, `Figure 2.`). 파일명의 lecture-scoped ID와 독립적으로 관리한다.

### 7.4. 이미지 경로

이미지 파일은 문서와 같은 폴더 내 `images/` 서브디렉토리에 저장한다.

```
020_notes/
  lec-001_notes.md
  images/
    fig-001-001.png
    fig-001-002.png
```

---

## 8. 테이블

### 8.1. 사용 기준

테이블은 항목 비교, 옵션 나열, 매핑 관계 표현에 사용한다. 단순 나열은 bullet list를 사용한다.

### 8.2. 형식 규칙

테이블 작성 시 아래 규칙을 따른다.

- 헤더 행은 반드시 포함한다
- 기본 정렬은 좌정렬이며, 숫자 열은 우정렬을 사용한다
- 셀 내용은 개조식으로 간결하게 작성하며 긴 문장은 본문에서 설명한다

```markdown
| 항목 | 설명 | 비고 |
|---|---|---|
| learning rate | 파라미터 갱신 크기 | 0.001 권장 |
| batch size | 미니배치 크기 | GPU 메모리에 따라 조정 |
```

---

## 9. Jupyter Book (MyST) 규칙

### 9.1. 헤더 구조

Jupyter Book 페이지에서 H1(`#`)은 페이지 제목으로만 사용하며 페이지당 하나만 허용한다.

### 9.2. 헤더 건너뜀 금지

H1 다음에 H3를 직접 사용하면 빌드 경고(`non-consecutive header`)가 발생하므로 금지한다. H2를 반드시 거쳐야 한다.

### 9.3. Overview / Contents 서브섹션

강의 노트의 Overview, Contents 섹션은 `###` 헤더 대신 굵은 글씨를 사용한다.

```markdown
**Overview**

강의 내용 요약을 문장형으로 작성한다.

**Contents**

- 항목 1
- 항목 2
```

### 9.4. remove-cell 태그

Jupyter Book 빌드 시 출력에서 제외할 셀에는 `remove-cell` 태그를 사용한다. `rcParams` 셀과 output 설정 셀 모두에 적용한다.

### 9.5. 이미지 중앙 정렬

이미지 중앙 정렬은 `_static/custom.css`에서 처리한다.

```css
p:has(img) + p { text-align: center; }
```

### 9.6. _toc.yml 구조

Figure 노트북은 Notes 페이지의 서브섹션으로 중첩한다.

```yaml
- file: lec-001_notes
  sections:
    - file: lec-001_figures
```

---

## 10. 참고문헌

### 10.1. 형식

참고문헌은 문서 마지막 섹션에 번호 목록으로 작성한다.

```markdown
## 10. 참고문헌

[1] Author, A. (Year). *Title of the paper*. Journal Name, vol(issue), pp.
[2] Author, B. (Year). *Book Title*. Publisher.
[3] URL: https://example.com (accessed: YYYY-MM-DD)
```

### 10.2. 본문 인용

본문에서 참고문헌을 인용할 때는 `[번호]` 형식을 사용한다.

```markdown
이 방법은 PatchCore [1] 를 기반으로 한다.
수렴 조건은 integral test [2] 로 확인할 수 있다.
```

### 10.3. BibTeX (LaTeX/PDF 출력 시)

LaTeX/PDF 출력 대상 문서는 `.bib` 파일을 별도로 관리하고 `\cite{}` 명령을 사용한다.

```latex
이 방법은 PatchCore \cite{roth2022towards} 를 기반으로 한다.
```