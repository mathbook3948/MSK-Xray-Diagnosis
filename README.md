# 반려동물 근골격계 X-ray 분류 모델

## 소개
반려동물(개, 고양이)의 근골격계 X-ray 이미지를 분석하여 정상(NOR)과 근골격계 이상(Mu05, Mu06, Mu07)을 분류하는 딥러닝 모델입니다. TensorFlow를 기반으로 ResNet152V2를 활용하였습니다.

## 모델 다운로드
<a href="https://drive.google.com/drive/folders/1OcVEyn9CKnmMJy67T7yGhyklZOvVY-jz?usp=sharing">Google Drive</a>

## 데이터셋
- X-ray 영상 데이터
- 클래스 구성:
  - **NOR**: 정상 (Normal)
  - **Mu05**: 슬개골탈구
  - **Mu06**: 전십자인대파열
  - **Mu07**: 추간판질환

## 모델 구조
- **기반 모델**: ResNet152V2
- **입력 크기**: (384, 384, 1) (Grayscale X-ray 이미지)
- **출력 레이어**: Softmax 기반 다중 클래스 분류
- **손실 함수**: Categorical Crossentropy
- **최적화 알고리즘**: SGD(확률적 경사 하강법)
- **평가지표**: Accuracy, Precision, Recall, AUC

## 혼동 행렬 분석
![image](https://github.com/user-attachments/assets/5d1d1421-7ff8-42b0-b266-c4aa405f602b)
- **NOR 클래스**: 정확하게 분류되었지만 일부 Mu05, Mu06, Mu07로 잘못 분류됨
- **Mu05 클래스**: 대부분 정확히 예측되었으나 NOR로 오분류된 경우 있음
- **Mu06, Mu07 클래스**: 학습용 샘플 수가 적어 NOR로 오분류되는 경향이 있음

## 개선점
- 절대적인 샘플의 수가 적어 정확도가 안 나온다고 판단하고 학습을 중단
- 추가적인 데이터 확보, 또는 오버샘플링이 필요
