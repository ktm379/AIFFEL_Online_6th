# AIFFEL Campus Online Code Peer Review Templete
- 코더 : 김태민
- 리뷰어 : 이명준

# PRT(Peer Review Template)
- [X]  **1. 주어진 문제를 해결하는 완성된 코드가 제출되었나요?**
    - 문제에서 요구하는 최종 결과물이 첨부되었는지 확인
    - 문제를 해결하는 완성된 코드란 프로젝트 루브릭 3개 중 2개, 퀘스트 문제 요구조건 등을 지칭
        - 해당 조건을 만족하는 코드를 캡쳐해 근거로 첨부
        - 스티커를 합성하진 못했지만 대부분의 루브릭을 완성했고, 학습 역시 오랜시간 진행하면서 학습의 진행을 보다 잘 확인할 수 있어서 리뷰어도 재밌게 코드를 볼 수 있었다.
    
- [X]  **2. 전체 코드에서 가장 핵심적이거나 가장 복잡하고 이해하기 어려운 부분에 작성된 주석 또는 doc string을 보고 해당 코드가 잘 이해되었나요?**
    - 해당 코드 블럭에 doc string/annotation이 달려 있는지 확인
    - 해당 코드가 무슨 기능을 하는지, 왜 그렇게 짜여진건지, 작동 메커니즘이 뭔지 기술.
    - 주석을 보고 코드 이해가 잘 되었는지 확인
        - 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부합니다.
        - 아래와 같이 어려운 개념을 중간중간 정리하면서 잘 설명했다
> jaccard 두 집합을 통해 유사도를 측정하는 방식 중 하나 두 집합의 교집합을 두 집합의 합집합으로 나눈다. 따라서 jaccard 유사도는 0과 1사이의 값을 가지며, 서로 비슷하면 1에 근접한다.

- [X]  **3. 에러가 난 부분을 디버깅하여 문제를 “해결한 기록을 남겼거나”, ”새로운 시도 또는 추가 실험을 수행”해봤나요?**
    - 문제 원인 및 해결 과정을 잘 기록하였는지 확인
    - 문제에서 요구하는 조건에 더해 추가적으로 수행한 나만의 시도, 
    실험이 기록되어 있는지 확인
        - 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부합니다.
```
import pickle

model_save_path = os.path.join(PROJECT_PATH, 'saved_model.h5')
history_path = os.path.join(PROJECT_PATH, 'history.pkl')

# 모델 저장
model.save(model_save_path)

# 학습 히스토리 저장
with open(history_path, "wb") as f:
    pickle.dump(history, f)
```
        
- [X]  **4. 회고를 잘 작성했나요?**
    - 주어진 문제를 해결하는 완성된 코드 내지 프로젝트 결과물에 대해
    배운점과 아쉬운점, 느낀점 등이 기록되어 있는지 확인
    - 전체 코드 실행 플로우를 그래프로 그려서 이해를 돕고 있는지 확인
        - 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부합니다.
```
왜 bar하고 plot이 두개 같이 나오지?
history_load['epoch']를 안넣으면 60000이 나온다.
전체데이터에 대한 배치의 step 만큼 계속 저장돼서 이렇게 나온것같다..
저장을 잘못한 것 같다...
다시 학습하기에는 시간이 부족함...
```     

        
- [X]  **5. 코드가 간결하고 효율적인가요?**
    - 파이썬 스타일 가이드 (PEP8) 를 준수하였는지 확인
    - 하드코딩을 하지않고 함수화, 모듈화가 가능한 부분은 함수를 만들거나 클래스로 짰는지
    - 코드 중복을 최소화하고 범용적으로 사용할 수 있도록 함수화했는지
        - 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부합니다.
```
EPOCHS = 150
history = {'epoch': [], 'batch': [], 'total_loss': [], 'loc_loss': [], 'class_loss': []}

for epoch in range(0, EPOCHS):
    for step, (inputs, labels) in enumerate(train_dataset.take(steps_per_epoch)):
        load_t0 = time.time()
        total_loss, losses = train_step(inputs, labels)
        load_t1 = time.time()
        batch_time = load_t1 - load_t0

        # 결과 기록
        history['epoch'].append(epoch + 1)
        history['batch'].append(step + 1)
        history['total_loss'].append(total_loss)
        history['loc_loss'].append(losses['loc'])
        history['class_loss'].append(losses['class'])

        # 출력
        print(f"\rEpoch: {epoch + 1}/{EPOCHS} | Batch {step + 1}/{steps_per_epoch} | Batch time {batch_time:.3f}
```


# 참고 링크 및 코드 개선
```
# 코드 리뷰 시 참고한 링크가 있다면 링크와 간략한 설명을 첨부합니다.
# 코드 리뷰를 통해 개선한 코드가 있다면 코드와 간략한 설명을 첨부합니다.
```
