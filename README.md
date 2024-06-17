# 2022년 AWS DeepRacer Championship 인천
제2회 대한민국 인공지능(AI) 융합 자율주행 경진대회 [AWS DeepRacer Championship 리그]

## 공모 내용
 인공지능 자율주행 장비(딥레이서)를 활용한 AI융합 아이디어 경진대회

## 대회 진행
### 트랙
<img src="https://github.com/khw274/DeepRacer-Incheon-2023/assets/125671828/198cfcb0-e954-4489-a87d-52998666ac7f" width="600" height="400"/>

### 예선
#### 보상함수 코드 설계

#### 하이퍼 파라미터 
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
기본으로 설정된 하이퍼파라미터 적용

#### 조향각과 조향각별 속도
```
Action space type: Continuous

Action space

Steering angle (°)    Speed (m/s)
[ 30 : -10 ]	      [ 1.50 : 3 ]
```
![제목 없음](https://github.com/khw274/DeepRacer-Incheon-2022/assets/125671828/c91a6495-aee7-45d5-bcce-12f6f8c862e5)
