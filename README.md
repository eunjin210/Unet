## Unet의 경량화 기법

## 개요
초음파 이미지로 학습하는 U-Net 모델의 경량화를 위해 구현한 모델을 소개한다. 구현 모델은 **Knowledge Distillation**(Teacher: Dilated Convolution, Student: Group Convolution)+**Pruning** 과 **Group Convolution + Pruning** 모델이다


## 데이터 셋
데이터 셋은 총 608개의 이미지와 이에 대응하는 바이너리 마스크 이미지로 구성되어 있다.
- **이미지**: 특정 해부학적 구조를 포착한 초음파 스캔 영상.

![image](https://github.com/user-attachments/assets/9760f86c-bd32-44b6-8b19-d015dec739a6)

- **마스크 이미지**: 각 이미지에서 관심 영역(ROI, Region of Interest)을 나타내는 이진 마스크.

![image](https://github.com/user-attachments/assets/30b76956-e391-4f35-bf3c-38cbd13a4994)




## 구현 모델
### 1) Knowledge Distillation (Teacher: Dilated Convolution, Student: Group Convolution) + Pruning
- **Knowledge Distillation**을 활용하여 Teacher 모델의 높은 정확도를 Student 모델에 전달
- **Pruning**을 통해 Student 모델을 추가적으로 경량화하여 계산 효율성을 향상
   - layer의 각 가지에 가중치를 받아와서, 가중치가 일정 수 이하인 것을 0으로 만드는 방식으로 변형하여 모델을 구현

### 2) Group Convolution + Pruning
1. **Group Convolution**:
   - 입력 특징 맵을 그룹으로 나누어 각 그룹에서 독립적으로 합성곱 연산 수행.
   - 계산량 감소와 파라미터 수 감소.

2. **Pruning**:
   - 중요도가 낮은 가중치를 제거하여 계산량 최적화.
   - 임계값 이하의 가중치를 0으로 설정.


---

## 6. 요구사항 (Requirements)



### **설치 방법**
필요한 패키지는 다음 명령어로 설치할 수 있습니다:
```bash
pip install -r requirements.txt
```

### \

