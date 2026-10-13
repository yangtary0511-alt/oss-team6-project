# GPU의 역할과 작동 원리

> GPU는 많은 데이터를 병렬로 처리하는 그래픽과 대규모 연산에 특화된 하드웨어이다.

## 목차
- [1. GPU란 무엇인가?](#1-gpu란-무엇인가)
- [2. GPU VS CPU](#2-gpu-vs-cpu)
- [3. GPU가 화면을 만드는 과정](#3-gpu가-화면을-만드는-과정)
- [4. VRAM의 역할](#4-vram의-역할)
- [5. 정리](#5-정리)

## 1. GPU란 무엇인가?

**GPU(Graphics Processing Unit)** 은 컴퓨터에서 이미지, 영상을 표현하는 데 필요한 연산을 수행하는 그래픽 처리 장치이다. 모니터로 보게 되는 화면이나 입체적인 그래픽, 특수 효과들은 **벡터·행렬 연산과 병렬 연산**을 거쳐 만들어진다. GPU는 이러한 연산을 효율적으로 처리하는 하드웨어 장치이다.

흔히 GPU라고 하면 그래픽카드와 같은 의미로 사용하는 경우가 많지만, 엄밀히 말하면 둘은 서로 다른 구분되는 개념이다.

- **GPU:** 연산을 수행하는 반도체 칩
- **그래픽카드:** GPU에 그래픽 메모리, 전원 공급 회로, 냉각장치 등을 결합한 하드웨어 장치


![NVIDIA AD102 GPU](https://github.com/user-attachments/assets/7c68ab99-284c-4186-85dc-2f0c2e4ecde1)

*그림 1. NVIDIA GeForce RTX 4090에 사용되는 AD102 GPU chip*

---

![ASUS ROG Strix GeForce RTX 4090 그래픽카드](https://upload.wikimedia.org/wikipedia/commons/7/76/Asus_Strix_RTX_4090.jpg)

*그림 2. ASUS ROG Strix GeForce RTX 4090 그래픽카드*

## 2. GPU VS CPU

CPU는 컴퓨터의 전반적인 동작을 제어하고 명령어를 처리하는 하드웨어이다.

반면 GPU는 **병렬 연산**에 최적화되어 있으며, GPU에서 연산을 처리하기 위해 다수의 연산 장치를 이용한다. 많은 데이터에 비슷한 연산을 적용하는 데 특화되어 있는 하드웨어이다.

| 구분 | CPU | GPU |
|---|---|---|
| 설계의 중점 | 명령어 처리 및 제어 | 많은 연산을 병렬로 처리 |
| 특화된 작업 | 순차적인 작업, 조건 분기 | 행렬 및 벡터의 연산 |
| 활용 | OS, 응용 프로그램 실행 | 그래픽 렌더링, 인공지능 연산 |

> CPU와 GPU는 서로 다른 강점을 가진 서로 대체될 수 없는 하드웨어이다.

## 3. GPU가 화면을 만드는 과정

## 4. VRAM의 역할

## 5. 정리


**이미지 출처**
- 그림 1: Fritzchens Fritz, Wikimedia Commons (CC0 1.0)
- 그림 2: Benlisquare, Wikimedia Commons (CC BY-SA 4.0)
