# Pacman Reinforcement Learning

## Brief
인공지능 과목 중간 및 기말 프로젝트 코드입니다. MDP를 풀고 Q-Learning을 통해 Pacman 게임을 자동으로 플레이하는 AI를 구현했습니다.

## Mission
MDP를 위한 Value iteration 구현. Q-Learning을 위한 Q-Value iteration 구현. 실제 pacman 게임에 Q-Learning 적용.

## Environment
- WSL 1
- Ubuntu 18.04
- python 2.7
- [Xming](https://sourceforge.net/projects/xming/files/latest/download) (if using WSL)

## Usage
0. Run Xming(WSL)
    ```console
    $export DISPLAY=localhost:0.0
    ```
1. To see how value iteration works
    ```console
    $python2.7 gridworld.py -a value -i 100 -k 10
    ```
2. To see how Q-Learning works   
    
    manual
    ```console
    $python2.7 gridworld.py -a q -k 5 -m
    ```
    automatic
    ```console
    $python2.7 gridworld.py -a q -k 100
    ```
3. To see how Q-Learning AI play pacman   
    training : 2000, test : 10 (displaying), layout : smallGrid
    ```console
    $python2.7 pacman.py -p PacmanQAgent -x 2000 -n 2010 -l smallGrid
    ```

## Value iteration - `valueIterationAgents.py`
주어진 MDP에서 value iteration 진행.   
    
```python
__init__(self, mdp, discount = 0.9, iterations = 100) # 실제 value iteration
computeActionFromValues(self, state)                  # action에 따른 value 계산
computeQValueFromValues(self, state, action)          # value값에서 Q-value 계산
```

## Q-Learning - `qlearningAgents.py`
실제 action을 취해가며 MDP 학습.   
```python
computeValueFromQValues(self, state)           # 현재 상태에서 value 계산
computeActionFromQValues(self, state)          # Q-value에 따른 최적의 action 계산
getAction(self, state)                         # 존재하는 다음 상태로 action 선택
update(self, state, action, nextState, reward) # 다음 상태로 업데이트
```

프로젝트는 UC Berkeley의 CS-188 수업의 3번째 프로젝트와 동일합니다.