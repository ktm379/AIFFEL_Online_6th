# AIFFEL Campus Online Code Peer Review Templete
- 코더 : 김태민
- 리뷰어 : 김민규


# PRT(Peer Review Template)
---
- [x]  **1. 주어진 문제를 해결하는 완성된 코드가 제출되었나요?**

| 평가문항                                                                | 상세기준                                                                         | 달성여부 |
| ----------------------------------------------------------------------- | -------------------------------------------------------------------------------- | -------- |
| 1. CutMix와 MixUp 기법을 ResNet50 분류기에 성공적으로 적용하였는가?     | CutMix와 MixUp을 적용한 데이터셋으로 훈련한 각각의 ResNet 모델이 수렴하였다.     | o        |
| 2. 다양한 실험을 통해 태스크에 최적인 Augmentation 기법을 찾아내었는가? | 각 Augmentation 기법을 적용하고, 그에 따른 성능 비교 분석 및 문제점을 서술하였음 | o        |
|3. 여러가지 Augmentation 기법을 적용한 결과를 체계적으로 비교분석하였는가?|기본 Augmentation, CutMix, MixUp이 적용된 결과를 시각화와 함께 체계적으로 분석하였다.|o          |

- 1번
![image](https://github.com/ktm379/AIFFEL_Online_6th/assets/68997408/fa31329e-d051-444a-b303-ea58b0bad4e7)

- 2, 3번
![image](https://github.com/ktm379/AIFFEL_Online_6th/assets/68997408/70a60656-99bb-42f4-9463-5371af98d983)

---
    
- [x]  **2. 전체 코드에서 가장 핵심적이거나 가장 복잡하고 이해하기 어려운 부분에 작성된 
주석 또는 doc string을 보고 해당 코드가 잘 이해되었나요?**

- cutmix 관련 함수
![image](https://github.com/ktm379/AIFFEL_Online_6th/assets/68997408/9ddd7b50-2b3d-4621-9be6-6e4291d9e096)



---
- [x]  **3. 에러가 난 부분을 디버깅하여 문제를 “해결한 기록을 남겼거나” 
”새로운 시도 또는 추가 실험을 수행”해봤나요?**

![image](https://github.com/ktm379/AIFFEL_Online_6th/assets/68997408/63be5cb0-ab01-46e6-b8a9-7777ffe68340)



---


- [x]  **4. 회고를 잘 작성했나요?**



![image](https://github.com/ktm379/AIFFEL_Online_6th/assets/68997408/19f9ac07-7d2a-44ce-be87-b05fbc43b22a)


---
        
- [x]  **5. 코드가 간결하고 효율적인가요?**


- 코드가 깔끔하게 작성됨
![image](https://github.com/ktm379/AIFFEL_Online_6th/assets/68997408/0a132353-7b0f-45da-8991-62224ee55218)

---

# 참고 링크 및 코드 개선

- 모델 학습 중에 callback 함수를 이용해서 모델을 저장해, 학습을 효율적으로 관리할 수 있었습니다!
```python
model_checkpoint_callback = tf.keras.callbacks.ModelCheckpoint(filepath=save_path,
                                                               save_weights_only=False,
                                                               monitor='val_accuracy',
                                                               mode='min',
                                                               save_best_only=False)
```



