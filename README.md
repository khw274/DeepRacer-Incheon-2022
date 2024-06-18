# 2022년 AWS DeepRacer Championship 인천
제2회 대한민국 인공지능(AI) 융합 자율주행 경진대회 [AWS DeepRacer Championship 리그]

## 공모 내용
 인공지능 자율주행 장비(딥레이서)를 활용한 AI융합 아이디어 경진대회

## 대회 진행
### 트랙
<img src="https://github.com/khw274/DeepRacer-Incheon-2023/assets/125671828/198cfcb0-e954-4489-a87d-52998666ac7f" width="600" height="400"/>

### 예선
#### 보상함수 코드 설계
보상을 주는 기준을 5가지로 구분
```
1. 차량의 모든 바퀴가 트랙 위에 있는가?
2. 속도가 2 이상인가?
3. 차량이 트랙 중심에서 30% 이내로 위치하는가?
4. 자동차가 올바른 방향으로 핸들을 돌리는가?
5. 트랙 방향과 현재 차량의 방향 간 차이가 작은가?
```
5가지 중 핵심은 차량이 트랙의 중심에 있으면서 트랙을 빠져나가지 않는 것이다.

트랙의 중심을 안정적으로 따라가지만 커브 구간에서 아웃코스를 타 라인을 이탈하거나 기록이 늦어지는 단점을 발견했다. 이를 해결하기 위해 조향각을 수정하였다.
#### 훈련 
총 1시간 훈련을 진행하였고 다음과 같은 보상 함수 그래프를 도출해냈다.
<img src="https://github.com/khw274/DeepRacer-Incheon-2022/assets/125671828/2c95f7dc-a58c-4447-9fc3-ab0f4601d4e9" width="600" height="500"/>


#### 하이퍼 파라미터 
기본으로 설정된 하이퍼파라미터 적용

```
(Hyperparameter)                                                        (Value)
Gradient descent batch size	                                        64
Entropy	                                                                0.01       
Discount factor	                                                        0.999
Loss type	                                                        Huber
Learning rate	                                                        0.0003
Number of experience episodes between each policy-updating iteration    20
Number of epochs	                                                10
```

#### 조향각과 조향각별 속도
대회 맵의 특성상 왼쪽으로 가는 경향이 많음, 또한 중앙선 추종시 커브길에서의 도로 이탈을 방지하고자 조향각을 좌측 중심으로 설정했다.

```
Action space type: Continuous

Action space

Steering angle (°)    Speed (m/s)
[ 30 : -10 ]	      [ 1.50 : 3 ]
```
![제목 없음](https://github.com/khw274/DeepRacer-Incheon-2022/assets/125671828/c91a6495-aee7-45d5-bcce-12f6f8c862e5)
