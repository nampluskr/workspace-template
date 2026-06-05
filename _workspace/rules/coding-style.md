# 코딩 스타일 가이드

워크스페이스 내 코드 작성 시 적용되는 통합 규칙 및 형식 지침이다.

> 생성일시: 260605-220755
> 수정일시: 260606-074638
> 주제: Development Environment and Tools

---

**목차**

1. [코드 주석](#1-코드-주석)
2. [코드 블록](#2-코드-블록)
3. [Jupyter Notebook 규칙](#3-jupyter-notebook-규칙)

---

## 1. 코드 주석

### 1.1. 주석 언어

코드 내 주석은 영어로만 작성한다.

```python
# Compute the mean of the input tensor
mean = x.mean(dim=0)
```

---

## 2. 코드 블록

### 2.1. 언어 명시

코드 블록은 항상 언어를 명시한다. 언어를 특정할 수 없는 경우 `text`를 사용한다.

````markdown
```python
```bash
```powershell
```cpp
```json
```yaml
```markdown
```text
````

### 2.2. 경로 표기

Python 코드 내 경로는 `os.path` 방식을 사용한다. `pathlib.Path`는 사용하지 않는다.

```python
# Correct
import os
path = os.path.join("data", "train", "images")
base = os.path.dirname(os.path.abspath(__file__))

# Incorrect
from pathlib import Path
path = Path("data") / "train" / "images"
```

### 2.3. 코드 블록 내 주석

주석은 영어로만 작성하며 블록 상단에 목적을 간략히 기술한다.

```python
# Load dataset and apply preprocessing transforms
dataset = ImageFolder(root=data_dir, transform=transform)
```

### 2.4. 실행 가능한 명령어

셸 명령어는 실제 실행 가능한 형태로 작성하며, 필요한 경우 예상 출력을 함께 제시한다.

```bash
conda activate pytorch_env
python train.py --config config.yaml
```

```text
[Expected output]
Epoch 1/50: loss=0.4231, acc=0.8120
```

---

## 3. Jupyter Notebook 규칙

### 3.1. 셀 구성 원칙

Figure 생성 노트북은 아래 순서로 셀을 구성한다.

1. Markdown 셀: 노트북 제목 및 경로
2. Code 셀: `rcParams` 설정 (태그: `remove-cell`)
3. Code 셀: output 설정 (태그: `remove-cell`)
4. Code 셀: 공유 스타일 변수 정의
5. 반복: Markdown 셀(Figure 번호/캡션) + Code 셀(Figure 코드)

### 3.2. rcParams 설정

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

### 3.3. 공유 스타일 변수

스타일 변수는 `rcParams` 셀 이후 별도 셀에서 정의한다.

```python
# Shared style variables for all figures
FS_LABEL = 12       # axis label font size
FS_TICK  = 10       # tick label font size
LW_CURVE = 1.8      # curve line width
MS_ARROW = 12       # arrow marker size
C_MAIN   = "#2c7bb6"  # main curve color
C_FILL   = "#d7ecf7"  # fill color
```

### 3.4. 레이블 언어

matplotlib의 모든 레이블(축 이름, 범례, 제목)은 영어 또는 LaTeX 전용으로 작성한다. 한국어 텍스트는 matplotlib에서 사용하지 않는다.

### 3.5. Figure 저장

Figure 저장 경로는 `os.path` 방식을 사용한다.

```python
import os

output_dir = os.path.join("images")
os.makedirs(output_dir, exist_ok=True)
fig.savefig(os.path.join(output_dir, "fig-001-001.png"), bbox_inches="tight")
```
