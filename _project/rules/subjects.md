# 주제 분류 체계

이 문서는 워크스페이스에서 공통으로 사용하는 주제 분류 기준을 정의한다.
문서 작성, 파일명, 태그, frontmatter 키워드를 결정할 때 이 분류를 기준으로 삼는다.

> 생성일시: 260605-220755
> 수정일시: 260607-160000
> 주제: Development Environment and Tools

**목차**

1. [개요](#1-개요)
2. [주제 분류 목록](#2-주제-분류-목록)
3. [주제별 세부 내용](#3-주제별-세부-내용)

## 1. 개요

전체 분류는 연구, 학습, 강의자료, 개발환경 문서화를 포괄하도록 구성한다.
각 subject code는 문서 frontmatter 태그, 파일명 접두사, 색인, 검색 키워드에 활용할 수 있다.

Subject code를 사용하는 방식은 다음과 같다.

- 문서 메타정보 태그 예시: `태그: ML, classification, pytorch`
- 폴더명 접두사 예시: `ml-classification/`, `nlp-tokenization/`
- 파일명 접두사 예시: `ml_image_classifier.py`, `nlp_tokenizer.md`

## 2. 주제 분류 목록

현재 정의된 주제 분류 코드와 전체 Subject 명칭은 다음과 같다.

| No | Subject Code | Subject Name |
|---:|---|---|
| 01 | `MATH` | Mathematics |
| 02 | `PHYS` | Physics |
| 03 | `NA` | Numerical Analysis |
| 04 | `ML` | Machine Learning |
| 05 | `CV` | Computer Vision |
| 06 | `NLP` | Natural Language Processing |
| 07 | `CS` | Computer Science |
| 08 | `DEV` | Development Environment and Tools |
| 09 | `MISC` | Miscellaneous |

## 3. 주제별 세부 내용

각 분류 코드에 해당하는 주제가 다루는 세부 내용을 정리한다.

### 3.1. [MATH] Mathematics

해석학(Analysis)은 수학의 핵심 분야로, 실수 체계에서 수열과 급수의 수렴, 연속성, 미분가능성, Riemann 적분을 엄밀하게 다룬다. Real Analysis는 함수의 균등수렴과 거리공간의 위상적 성질을 포함하며, Complex Analysis로 확장되면 유수 정리(residue theorem)와 등각사상(conformal mapping)을 통한 강력한 적분 계산 도구를 제공한다.

대수학 분야에서는 Linear Algebra를 중심으로 벡터공간, 선형사상, 고유값 분해, 행렬 분해(QR / SVD / Cholesky)를 다룬다. 이 내용은 수치해석과 머신러닝의 수학적 기초가 된다. Vector Calculus에서는 gradient·divergence·curl과 Stokes / Gauss 정리를 다루며, 물리학·전자기학과 직접 연결된다.

미분방정식은 ODE와 PDE를 모두 포함한다. Fourier 급수와 변환을 통해 열방정식·파동방정식·Laplace 방정식의 해법을 다루며, 물리 현상의 수학적 모델링에 활용된다.

Special Functions 분야에서는 Gamma 함수, Bessel 함수, Legendre 다항식처럼 수리물리에서 자주 등장하는 함수들의 성질과 점화식을 다룬다. Riemann Zeta Function은 별도의 세부 항목으로, 해석적 연속·비자명 영점·소수 분포와의 관계를 중심으로 다룬다.

- Real Analysis
- Complex Analysis
- Vector Calculus
- Linear Algebra
- Differential Equations
- Mathematical Physics
- Special Functions
- Riemann Zeta Function

### 3.2. [PHYS] Physics

전자기학(Electromagnetism)은 물리학에서 가장 중요한 분야 중 하나로, 정전기학(Electrostatics)과 정자기학(Magnetostatics)을 출발점으로 시간 변화하는 전자기장의 동역학(Electrodynamics)까지 다룬다. Maxwell 방정식을 중심으로 전자기파의 발생과 전파를 이해하며, 수치 시뮬레이션과 직접 연결된다.

양자역학(Quantum Mechanics)은 파동함수, Schrödinger 방정식, 연산자 이론을 중심으로 미시 세계의 물리 법칙을 기술한다. 이 분야는 수학의 Hilbert 공간 이론 및 특수함수(Legendre·Hermite 다항식)와 밀접하게 연결된다.

유체역학(Fluid Dynamics)과 플라즈마 물리(Plasma Physics)는 연속체 역학의 응용 분야다. Navier-Stokes 방정식을 기반으로 유체 흐름을 분석하며, 플라즈마에서는 전자기장과 하전 입자의 상호작용을 다룬다. Plasma Simulation은 FDM / PIC 등 수치 기법을 활용하여 플라즈마 거동을 모사한다.

- Electromagnetism
- Electrostatics
- Magnetostatics
- Electrodynamics
- Quantum Mechanics
- Fluid Dynamics
- Plasma Physics
- Plasma Simulation

### 3.3. [NA] Numerical Analysis

수치해석은 해석적 방법으로 풀기 어려운 수학 문제를 컴퓨터 계산으로 근사하는 방법론을 다룬다. 비선형 방정식의 근 탐색(Newton-Raphson, bisection), 선형계(LU 분해, 반복법), 보간과 근사(Lagrange, spline)를 기초로 삼는다.

수치 미분·적분은 연속 연산을 이산화하는 핵심 기법이다. Gaussian quadrature, Runge-Kutta를 포함한 ODE 수치 풀이, 열방정식·파동방정식에 대한 FDM / FEM / FVM 등 PDE 수치 풀이까지 포괄한다. Particle Tracing은 전자기장 내 하전 입자 궤적을 수치적으로 추적하는 응용 분야다.

최적화(Optimization) 분야에서는 gradient descent 계열, 선형계획법, 제약 최적화를 다룬다. Pi Computation은 고정밀 수치 계산의 구체적 예시로 활용하며, Chaos and Fractals는 비선형 동역학 시스템과 자기유사 구조를 수치적으로 탐구한다.

- Nonlinear Equations
- Numerical Linear Algebra
- Interpolation and Approximation
- Numerical Differentiation
- Numerical Integration
- Ordinary Differential Equations
- Partial Differential Equations
- Optimization
- Finite Difference Method (FDM)
- Finite Element Method (FEM)
- Finite Volume Method (FVM)
- Particle Tracing
- Pi Computation
- Chaos and Fractals

### 3.4. [ML] Machine Learning

머신러닝은 데이터로부터 패턴을 학습하여 예측이나 의사결정을 수행하는 방법론을 다룬다. Classification과 Regression은 지도학습의 기본 태스크로, 각각 범주형·연속형 출력을 모델링한다. Clustering은 비지도학습의 대표 방법으로, 레이블 없이 데이터의 구조를 탐색한다.

Time Series Analysis는 시간적 순서를 가진 데이터의 패턴 파악과 예측을 다루며, 금융·센서·로그 데이터 분석에 활용된다. Anomaly Detection은 정상 패턴에서 벗어난 관측값을 탐지하는 기법으로, 제조 불량 검출·이상 거래 탐지 등에 적용된다. AutoML (PyCaret)은 전처리·모델 선택·하이퍼파라미터 탐색을 자동화하는 도구 활용을 다룬다.

- Classification
- Regression
- Clustering
- Time Series Analysis
- Anomaly Detection
- AutoML - PyCaret

### 3.5. [CV] Computer Vision

컴퓨터 비전은 이미지·영상 데이터에서 의미 있는 정보를 추출하는 딥러닝 응용 분야다. Image Preprocessing 단계에서는 OpenCV·torchvision·albumentations 등 라이브러리를 활용하여 정규화, 크기 변환, 데이터 증강을 수행한다.

핵심 태스크는 크게 세 가지다. Image Classification은 이미지 전체에 레이블을 부여하며, Image Segmentation은 픽셀 단위 분류를 수행한다. Object Detection은 이미지 내 객체의 위치(bounding box)와 클래스를 동시에 예측한다. Vision Anomaly Detection은 정상 이미지와의 편차를 측정하여 표면 결함 등의 이상을 식별한다.

Vision Backbones는 ResNet, ViT, EfficientNet 등 특징 추출에 사용되는 사전 학습 모델 구조를 다루며, Vision Datasets에서는 ImageNet, MVTec, COCO 등 벤치마크 데이터셋의 구성과 로딩 방식을 다룬다.

- Image Preprocessing: OpenCV / scikit-image / PIL / torchvision / augmentations
- Image Classification
- Image Segmentation
- Object Detection
- Vision Anomaly Detection
- Vision Backbones
- Vision Datasets

### 3.6. [NLP] Natural Language Processing

자연어 처리는 텍스트 데이터를 기계가 이해하고 생성할 수 있도록 처리하는 분야다. Text Preprocessing과 Tokenization은 원시 텍스트를 모델 입력 형태로 변환하는 기초 단계이며, Word Embeddings는 단어를 연속 벡터 공간에 표현하는 방법론을 다룬다.

Sequence Modeling에서는 RNN·LSTM 계열의 시퀀스 처리 구조를 다루며, Attention Mechanism과 Transformer 아키텍처로 이어진다. Transformer는 현대 언어 모델의 기반 구조로, BERT·GPT 계열의 Language Models가 이를 토대로 구축된다.

응용 분야로는 Text Classification, Text Generation이 있으며, Retrieval-Augmented Generation(RAG)은 외부 지식베이스를 언어 모델과 결합하는 기법이다. Hugging Face 생태계와 오픈소스 LLM 모델의 활용 방법도 포함한다.

- Text Preprocessing
- Tokenization
- Word Embeddings
- Sequence Modeling
- Attention Mechanism
- Transformer
- Language Models
- Text Classification
- Text Generation
- Retrieval-Augmented Generation
- Huggingface and Open LLM Models

### 3.7. [CS] Computer Science

컴퓨터 과학 분야는 프로그래밍 언어, 자료구조, 알고리즘, 소프트웨어 설계를 다룬다. Python Programming은 이 워크스페이스의 주 언어로, 과학 계산·데이터 분석·딥러닝 프레임워크 활용을 포함한다. C++ Programming은 성능이 중요한 시뮬레이션·임베디드 응용에 활용하며, 메모리 관리와 객체지향 설계를 다룬다.

Data Structures와 Algorithms는 효율적인 프로그램 작성의 기초로, 배열·트리·그래프·해시테이블과 정렬·탐색·동적 계획법을 포함한다. Design Patterns는 반복되는 소프트웨어 설계 문제에 대한 검증된 해법을 다루며, Test-Driven Development and Refactoring은 코드 품질 유지와 점진적 개선 방법론을 다룬다.

- Python Programming
- C++ Programming
- Data Structures
- Algorithms
- Design Patterns
- Test-Driven Development and Refactoring

### 3.8. [DEV] Development Environment and Tools

개발 환경과 도구는 실제 작업 생산성을 직접 결정하는 분야다. Git과 GitHub는 버전 관리와 협업 워크플로우(branch strategy, pull request, CI)를 다루며, VSCode는 에디터 확장, 원격 터널(VSCode Tunnel), 단축키 등 개발 환경 최적화를 다룬다.

문서화 도구로는 Jupyter Book v2(MyST Markdown 기반 웹북 생성), Markdown, LaTeX를 다룬다. 지식 관리 측면에서는 Obsidian과 PARA / Second Brain 방법론을 포함한다.

실행 환경 구성에서는 Anaconda 기반 Python 환경, C++ 빌드 환경, CUDA GPU 환경, WSL(Windows Subsystem for Linux) 설정을 다룬다. AI CLI Tools는 Claude Code, Codex 등 AI 보조 도구의 활용과 설정을 포함한다.

- Git
- GitHub: Development Process / Branch Strategy
- VSCode: Tips / Extensions / VSCode Tunnel
- Jupyter Book (version 1 vs. 2)
- Markdown
- LaTeX
- Obsidian
- PARA / Second Brain
- Python Environment
- C++ Environment
- CUDA Environment
- WSL / Anaconda
- Windows Development Environment
- AI CLI Tools

### 3.9. [MISC] Miscellaneous

Miscellaneous는 특정 분류에 귀속되지 않거나 아직 분류가 확정되지 않은 자료를 임시로 보관하는 공간이다. 두 개 이상의 분야에 걸치는 cross-domain 아이디어, 작업 중인 초안(Drafts), 개인 메모가 여기에 포함된다.

이 분류는 정식 분류가 결정될 때까지 자료의 위치를 보존하는 임시 저장소 역할을 하며, 일정 기간 후 적절한 분류로 이동하거나 삭제 여부를 검토한다.

- Temporary Notes
- Uncategorized Materials
- Cross-domain Ideas
- Personal Memos
- Reference Links
- Drafts
- Legacy Materials
