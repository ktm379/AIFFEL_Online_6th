# AIFFEL Campus Online Code Peer Review Templete
- 코더 : 김태민
- 리뷰어 : 이명준


# PRT(Peer Review Template)
- [X]  **1. 주어진 문제를 해결하는 완성된 코드가 제출되었나요?**
    - 문제에서 요구하는 최종 결과물이 첨부되었는지 확인
    - 문제를 해결하는 완성된 코드란 프로젝트 루브릭 3개 중 2개, 퀘스트 문제 요구조건 등을 지칭
        - 해당 조건을 만족하는 코드를 캡쳐해 근거로 첨부
        - 3가지 루브릭 달성 확인
    
- [X]  **2. 전체 코드에서 가장 핵심적이거나 가장 복잡하고 이해하기 어려운 부분에 작성된 주석 또는 doc string을 보고 해당 코드가 잘 이해되었나요?**
    - 해당 코드 블럭에 doc string/annotation이 달려 있는지 확인
    - 해당 코드가 무슨 기능을 하는지, 왜 그렇게 짜여진건지, 작동 메커니즘이 뭔지 기술.
    - 주석을 보고 코드 이해가 잘 되었는지 확인
        - 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부합니다.
        - 그냥 지나갈 수도 있는 함수에 대한 설명이 잘 되어있다
```
# train_json 파일을 여고, json 형식의 annotation 정보를 읽어온다.
with open(TRAIN_JSON) as train_json:
# json 파일을 python 데이터로 load한다.
train_annos = json.load(train_json)

# 1번째 annotation 정보를 예시로 선택하여 json 형식으로 출력
# indent = 2 옵션은 들여쓰기를 2칸으로 지정하여 가독성을 높임
json_formatted_str = json.dumps(train_annos[0], indent=2)

print(json_formatted_str)
```
        
- [X]  **3. 에러가 난 부분을 디버깅하여 문제를 “해결한 기록을 남겼거나” ”새로운 시도 또는 추가 실험을 수행”해봤나요?**
    - 문제 원인 및 해결 과정을 잘 기록하였는지 확인
    - 문제에서 요구하는 조건에 더해 추가적으로 수행한 나만의 시도, 실험이 기록되어 있는지 확인
        - 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부합니다.
     
```
이미 Ray를 초기화했는데
또 다시 ray.init()을 호출하면 문제가 발생한다.
이미 초기화된 ray를 종료하고 다시 초기화해야한다.
ray.shutdown()을 호출하여 ray를 종료한 후, ray.init()을 호출하면 된다.
RuntimeError Traceback (most recent call last) /tmp/ipykernel_31/2812350357.py in 3 4 # Ray 초기화 ----> 5 ray.init() 6 7 # TFRecord 경로 확인 및 생성

/opt/conda/lib/python3.9/site-packages/ray/_private/client_mode_hook.py in wrapper(args, kwargs) 87 if func.name != "init" or is_client_mode_enabled_by_default: 88 return getattr(ray, func.name)(args, kwargs) ---> 89 return func(*args, kwargs) 90 91 return wrapper

/opt/conda/lib/python3.9/site-packages/ray/worker.py in init(address, num_cpus, num_gpus, resources, object_store_memory, local_mode, ignore_reinit_error, include_dashboard, dashboard_host, dashboard_port, job_config, configure_logging, logging_level, logging_format, log_to_driver, namespace, runtime_env, _enable_object_reconstruction, _redis_max_memory, _plasma_directory, _node_ip_address, _driver_object_store_memory, _memory, _redis_password, _temp_dir, _lru_evict, _metrics_export_port, _system_config, _tracing_startup_hook, **kwargs) 838 return 839 else: --> 840 raise RuntimeError("Maybe you called ray.init twice by accident? " 841 "This error can be suppressed by passing in " 842 "'ignore_reinit_error=True' or by calling "

RuntimeError: Maybe you called ray.init twice by accident? This error can be suppressed by passing in 'ignore_reinit_error=True' or by calling 'ray.shutdown()' prior to 'ray.init()'.
```

- [X]  **4. 회고를 잘 작성했나요?**
    - 주어진 문제를 해결하는 완성된 코드 내지 프로젝트 결과물에 대해 배운점과 아쉬운점, 느낀점 등이 기록되어 있는지 확인
    - 전체 코드 실행 플로우를 그래프로 그려서 이해를 돕고 있는지 확인
        - 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부합니다.
        - <img width="887" alt="image" src="https://github.com/ktm379/AIFFEL_Online_6th/assets/129345591/f38b15e7-4abc-4edb-bc0a-a36e29a25ad8">

        
- [X]  **5. 코드가 간결하고 효율적인가요?**
    - 파이썬 스타일 가이드 (PEP8) 를 준수하였는지 확인
    - 하드코딩을 하지않고 함수화, 모듈화가 가능한 부분은 함수를 만들거나 클래스로 짰는지
    - 코드 중복을 최소화하고 범용적으로 사용할 수 있도록 함수화했는지
        - 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부합니다.
        - 클래스 구현부분
```
class SaveHistoryCallback(tf.keras.callbacks.Callback):
    def on_epoch_end(self, epoch, logs=None):
        # 현재 에폭의 히스토리를 저장
        with open(loss_save_path.format(epoch=epoch), 'wb') as file:
            pickle.dump(logs, file)
```


# 참고 링크 및 코드 개선
```
# 코드 리뷰 시 참고한 링크가 있다면 링크와 간략한 설명을 첨부합니다.
# 코드 리뷰를 통해 개선한 코드가 있다면 코드와 간략한 설명을 첨부합니다.
```
