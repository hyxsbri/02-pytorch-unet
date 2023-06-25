# PyTorch를 활용한 U-Net 모델링

![U-net-architecture](https://upload.wikimedia.org/wikipedia/commons/d/dc/U-net-architecture.png)

## 소개

* ISBI (International Symposium on Biomedical Imaging) 2012 EM (Electron Microscopy) Segmentation Challenge 에서 제공한 데이터 셋을 활용했습니다.  
* 프로젝트 목표: 전자 현미경 이미지에서 세포 및 세포 구성 요소를 정확하게 분할하는 알고리즘을 개발, 세포와 조직의 미세 구조 세분화
* 본 저장소는 데이터 셋을 U-Net 아키텍처에 적용하기 위한 구현 과정 및 결과물이 포함돼있습니다.

## 저장소 내용

### 1. `datasets` 폴더

`datasets` 폴더에는 훈련 및 평가에 사용되는 데이터셋이 포함되어 있습니다. 이 데이터셋은 U-Net 모델을 훈련하고 성능을 평가하는 데 사용됩니다.

#### test-volume.tif
* 테스트 데이터로 사용된 전자 현미경 이미지입니다.
* 세포와 그 구성 요소가 포함된 이미지로, 해당 이미지에 대해 자신의 알고리즘을 적용하여 세포 구분 및 분할 결과를 생성해야 합니다.

#### train-labels.tif
* 훈련 데이터로 사용된 이미지의 분할 레이블입니다.
* 훈련 이미지와 동일한 크기와 해상도를 갖습니다.
* `train-volume.tif` 파일과 함께 사용하여 알고리즘의 학습 및 성능 평가에 활용됩니다.
* 
#### train-volume.tif
* 훈련 데이터로 사용된 전자 현미경 이미지입니다.
* 세포와 그 구성 요소가 포함된 이미지로, 참가자들은 이 이미지에 대해 자신의 알고리즘을 훈련시키고 세포의 분할을 수행해야 합니다.
* 
### 2. `data_read.py`

`data_read.py` 스크립트는 입력 데이터를 읽고 전처리하는 역할을 담당합니다. 데이터셋을 로드하고 필요한 변환 또는 증강을 수행합니다. 

### 3. `dataset.py`

`dataset.py` 스크립트는 PyTorch의 Dataset 클래스를 활용하여 데이터셋을 구성하는 데 사용됩니다. 데이터셋을 로드하고 전처리된 데이터를 모델에 공급합니다.

### 4. `eval.py`

`eval.py` 스크립트는 훈련된 모델을 평가하는 데 사용됩니다. 저장된 모델 파라미터를 로드하고 설정한 평가 메트릭을 계산합니다.
  
### 5. `model.py`

`model.py` 스크립트는 U-Net 모델의 구현을 포함하고 있습니다. 이 스크립트는 U-Net 아키텍처를 정의하고 모델의 forward pass를 처리합니다.

### 6. `run_unet.ipynb`

* `run_unet.ipynb` 노트북 파일은 U-Net 모델의 실행 예시를 제공합니다. 데이터셋을 로드하고 모델을 초기화하며, 훈련 및 평가 과정을 수행하는 코드를 포함하고 있습니다.  
* `%load_ext tensorboard` TensorBoard를 활성화하는 라인입니다. 이를 통해 학습 과정 및 결과를 시각화했습니다.  
* `tensorboard --logdir='./drive/MyDrive/002-pytorch-unet/log` TensorBoard를 실행하고 로그 디렉토리를 지정합니다. 이 디렉토리에는 학습과 관련된 이벤트 및 요약 데이터가 저장됩니다.  
* `!python3 './drive/MyDrive/002-pytorch-unet/train.py' ...` 스크립트를 실행하여 U-Net 모델을 학습 및 테스트합니다. 다양한 인수와 함께 학습을 수행했습니다.  
* `--batch_size` 2, `--mode` 를 'test'로 설정 후 테스트 모드를 수행헀습니다.

### 7. `train.py`

* `train.py` 스크립트는 U-Net 모델을 훈련하는 데 사용됩니다. 데이터 로딩, 모델 초기화, 훈련 루프, 모델 파라미터 저장 등을 처리합니다.
* Adam 옵티마이저와 이진 분류 문제에서 사용되는 손실 함수인 nn.BCEWithLogitsLoss 를 손실 함수로 사용했습니다.
*  Binary Cross Entropy with Logits Loss 함수는 내부적으로 Sigmoid 활성화 함수와 Binary Cross Entropy Loss 를 종합합니다.


### 8. `util.py`

`util.py` 스크립트에는 유틸리티 함수들이 포함되어 있습니다. 이러한 함수들은 모델 훈련 및 평가에 유용하게 사용될 수 있습니다.

## 결과

* 총 12개의 배치에 대한 평균 테스트 손실(loss) 을 통해 설계한 U-Net 모델의 테스트 결과에 대한 평가를 진행했습니다.  
* 최종 AVERAGE TEST: BATCH 0012 / 0012 | LOSS 0.2004 를 기록했습니다.

