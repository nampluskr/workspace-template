# Python Coding Style Guide

## Overview

- 기반 표준: PEP8
- 적용 범위: NumPy 수치해석, PyTorch 딥러닝 프로젝트

## 1. 네이밍 Convention

| 항목 | 규칙 | 예시 |
|---|---|---|
| 변수명 | `snake_case` | `backbone_name`, `num_epochs` |
| 함수명 | `snake_case` | `get_trainer`, `load_backbone_weights` |
| 클래스명 | `PascalCase` | `QuadDataset`, `BaseTrainer` |
| 상수 | `UPPER_SNAKE_CASE` | `MAX_EPOCHS`, `DEFAULT_IMG_SIZE` |
| 멤버 변수 접두사 | 없음 | `self.name` (`m_name`, `name_` 금지) |
| private 접두사 | `_` (접근 제어 목적만) | `self._cache` |

### 도메인별 용어 규칙

| 잘못된 용어 | 올바른 용어 | 이유 |
|---|---|---|
| `val` | `valid` | split 명칭 통일 |
| `model_name` | `backbone_name` | 모델명과 백본명 구분 |

## 2. 경로 처리

`pathlib.Path` 사용 금지. `os.path` 사용.

```python
# Bad
from pathlib import Path
weight_path = Path(output_dir) / "model.pth"
config_dir = Path(base_dir) / "configs" / "paths.yaml"

# Good
import os
weight_path = os.path.join(output_dir, "model.pth")
config_dir = os.path.join(base_dir, "configs", "paths.yaml")
```

## 3. 함수 인자 전달

`**kwargs` 언팩킹 대신 명시적 인자 전달.

```python
# Bad
trainer_kwargs = {"backbone_dir": backbone_dir, "img_size": img_size}
trainer = TrainerClass(**trainer_kwargs)

# Good
trainer = TrainerClass(backbone_dir=backbone_dir, img_size=img_size)
```

## 4. 코드 포맷 — 세로 정렬 금지

등호(`=`), 콜론(`:`) 의 세로 정렬(vertical alignment) 금지.

```python
# Bad
backbone_name = "resnet50"
img_size      = 224
num_epochs    = 10
batch_size    = 32

# Good
backbone_name = "resnet50"
img_size = 224
num_epochs = 10
batch_size = 32
```

dict 리터럴도 동일하게 적용.

```python
# Bad
config = {
    "backbone" : "resnet50",
    "img_size" : 224,
    "epochs"   : 10,
}

# Good
config = {
    "backbone": "resnet50",
    "img_size": 224,
    "epochs": 10,
}
```

## 5. 타입 힌트 / 독스트링

요청 시에만 추가. 기본적으로 생략.

```python
# Default — no type hints, no docstring
def get_config(model_type, dataset, category, num_epochs):
    config = {
        "model_type": model_type,
        "dataset": dataset,
        "category": category,
        "num_epochs": num_epochs,
    }
    return config

# Only when explicitly requested
def get_config(model_type: str, dataset: str, category: str, num_epochs: int) -> dict:
    """Build training config.

    Args:
        model_type: Registered model key (e.g., "padim", "stfpm").
        dataset: Dataset name (e.g., "mvtec").
        category: Category name within dataset.
        num_epochs: Number of training epochs.

    Returns:
        Config dict.
    """
    ...
```

## 6. 주석

코드 내 주석은 영어로 작성하고, 필요한 경우에만 작성하고, 너무 자주 사용하여 코드를 읽는데 방해가 되지 않도록 한다. 핵심 코드 블럭을 구분하는 용도로 사용되는 것이 좋다.

```python
# Build output path using stage and backbone name
output_path = os.path.join(output_dir, f"{stage}-{backbone_name}.pth")

# Load pretrained weights before replacing head to avoid shape mismatch
load_backbone_weights(model, backbone_dir)
replace_head(model, num_outputs=8)
```

## 7. 출력 (print)

이모지 사용 금지. 상태 표시는 ASCII 텍스트 사용.

```python
# Bad
print(f"  {'OK' if ok else 'FAIL'} {lec_id}")
print(f"  {'완료 OK' if ok else '실패 FAIL'}")

# Good
print(f"  {'[OK]' if ok else '[FAIL]'} {lec_id}")
print(f"  {'[OK]' if exists else '[--]'} {fname}")
```

