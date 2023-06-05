# Pytorch를 활용한 UNet 모델링
## 2022.10.10 ~ 2022.10.30

![U-net-architecture](https://upload.wikimedia.org/wikipedia/commons/d/dc/U-net-architecture.png)

## 소개

이 저장소는 U-Net 아키텍처를 사용한 PyTorch CNN(Convolutional Neural Network) 구현 과정 및 결과물입니다.

## 저장소 내용

### 1. `datasets` 폴더

`datasets` 폴더에는 훈련 및 평가에 사용되는 데이터셋이 포함되어 있습니다. 이 데이터셋은 U-Net 모델을 훈련하고 성능을 평가하는 데 사용됩니다.

### 2. `data_read.py`

`data_read.py` 스크립트는 입력 데이터를 읽고 전처리하는 역할을 담당합니다. 데이터셋을 로드하고 필요한 변환 또는 증강을 수행합니다. 

### 3. `dataset.py`

`dataset.py` 스크립트는 PyTorch의 Dataset 클래스를 활용하여 데이터셋을 구성하는 데 사용됩니다. 데이터셋을 로드하고 전처리된 데이터를 모델에 공급합니다.

### 4. `eval.py`

`eval.py` 스크립트는 훈련된 모델을 평가하는 데 사용됩니다. 저장된 모델 파라미터를 로드하고, 정확도, 정밀도, 재현율, F1 스코어 등 다양한 평가 메트릭을 계산합니다. 이 스크립트는 모델의 성능에 대한 포괄적인 분석을 제공합니다.

### 5. `model.py`

`model.py` 스크립트는 U-Net 모델의 구현을 포함하고 있습니다. 이 스크립트는 U-Net 아키텍처를 정의하고 모델의 forward pass를 처리합니다.

### 6. `run_unet.ipynb`

`run_unet.ipynb` 노트북 파일은 U-Net 모델의 실행 예시를 제공합니다. 데이터셋을 로드하고 모델을 초기화하며, 훈련 및 평가 과정을 수행하는 코드를 포함하고 있습니다.  
`%load_ext tensorboard` TensorBoard를 활성화하는 라인입니다. 이를 통해 학습 과정 및 결과를 시각화했습니다.  
`tensorboard --logdir='./drive/MyDrive/002-pytorch-unet/log` TensorBoard를 실행하고 로그 디렉토리를 지정합니다. 이 디렉토리에는 학습과 관련된 이벤트 및 요약 데이터가 저장됩니다.


### 7. `train.py`

`train.py` 스크립트는 U-Net 모델을 훈련하는 데 사용됩니다. 데이터 로딩, 모델 초기화, 훈련 루프, 모델 파라미터 저장 등을 처리합니다.

### 8. `util.py`

`util.py` 스크립트에는 유틸리티 함수들이 포함되어 있습니다. 이러한 함수들은 모델 훈련 및 평가에 유용하게 사용될 수 있습니다.

## 결과

총 12개의 배치에 대한 평균 테스트 손실(loss) 을 통해 설계한 U-Net 모델의 테스트 결과에 대한 평가를 진행했습니다.  

AVERAGE TEST: BATCH 0012 / 0012 | LOSS 0.2004

