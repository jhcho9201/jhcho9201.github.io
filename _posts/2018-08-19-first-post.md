---
title: "모두를 위한 PG여행 가이드 후기 (수정중)"
date: 2018-08-25 13:19:00 -0400
categories: Seminar RL Reinforcementlearning RLKorea
---

1. 모두를 위한 PG여행 가이드
PG여행에서는 7개 논문에 대해 소개하였다. 정리팀, 구현팀 나누어서 프로젝트를 진행함. 행아웃을 통해 논문을 리뷰하였음.

- Policy Gradient 논문 : 어떻게 강화학습을 PG로 다룰 수 있는지에 대해 설명한 논문이다. PG이론을 정의하고 증명한 논문이다. RL부터 Actor critic까지 어떻게 연결할 수 있는지 설명하는 논문이다.
- DPG 논문 : Deterministic policy가 존재하는 것을 증명한 논문이다. 
- DDPG 논문 : 기존의 강화학습은 High dimentional task를 더 잘하기 위해 연구한 논문이다. Continuous control을 하기 위해 여러 방법을 제안한다. Artor-critic 접근과 DQN을 결합한다. 리플레이 버퍼와 타겟 Q 네트워크를 이용하여 잘 학습하게 되었다.
- TRPO 논문 : Trust Region Policy Optimization. 앞에 내용은 잘 알아듣지 못했다. 핵심은 아무런 제약없이 학습한다면 빠르게 학습하거나 좋은 학습을 할 수 없기 때문에 policy가 조금씩 변할 수 있도록 스텝사이즈를 찾고 lower bound를 구하고 최적화한다. 이런 과정을 반복하면서 학습한다. 
즉, 학습에 제약을 걸면서 policy를 학습한다.
- PPO 논문 : 
강화학습에 고려사항들 : 확장성이 있는지, 데이터 효율이 좋은지 ?, 하이퍼파라미터의 여부들.
DQN은 discrete에서는 잘되는데, continuous는 검증 안됨.
A3C는 데이터 효율성에서 robust가 보장되지 않음.
PPO에서는 clip을 사용하여 최적화를 한다. TRPO는 최적화를 여러번 나누어 했지만, PPO는 ??

구현한 논문 
- Vanilla Policy Gradient
- TNPG(Truncated Natural Policy Gradient)
- TRPO(Trust Region Policy Optimization)
- PPO()

Mujoco라는 물리 시뮬레이션 환경을 활용하여 알고리즘들을 사용해보았다. 
Vanilla는 학습에 오래 걸림.
TNPG는 생각보다 잘됨.
TRPO는 2000정도부터 잘되지만 편차가 좀 심한편임.
PPO는 성능이 확실히 좋음. 가장 잘 작동됨.
각 알고리즘을 12000 step에서 비교해보니 TRPO는 성능이 별로였음 (원인은 잘모르겠음). PPO가 베스트
80000 step에서보면 PPO가 베스트였다. Vanilla PG는 제약도 없고 시뮬레이션만 잘 할 수 있으면 좋은 성능을 발휘한다.

저자는 PPO를 사용하라고 한다.

Unity Walker Plane에서 PPO를 사용해보니 처음에는 걷지도 못했지만 점차 좋은 성능을 보이긴 했다. 
Unity Walker Curved에서 실험해보니 score 300부터는 뛰기 시작. 700일 때는 잘 걷는다.

질문
1. 파라미터는 튜닝했나요? PPO는 직접 구현해서 하이퍼파라미터를 튜닝해서 사용했음. 

후기 : 블로그를 사람들이 읽기 쉽게 정리하는데 어려웠다 논문마다 핵심 내용을 각각 요약했다. 블로그를 참조하면 좋을 것 같다. 수식 증명도 다 되어있어서 궁금하면 참조할 수 있다. 
"머리가 아프고 힘들수록 잘하고 있는겁니다."
