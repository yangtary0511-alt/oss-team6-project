# GPU의 역할과 작동 원리

> GPU는 많은 데이터를 병렬로 처리하는 그래픽과 대규모 연산에 특화된 하드웨어이다.

## 목차
- [1. GPU란 무엇인가?](#1-gpu란-무엇인가)
- [2. GPU VS CPU](#2-gpu-vs-cpu)
- [3. GPU가 화면을 만드는 과정](#3-gpu가-화면을-만드는-과정)
- [4. VRAM의 역할](#4-vram의-역할)
- [5. 정리](#5-정리)

## 1. GPU란 무엇인가?

**GPU(Graphics Processing Unit)** 은 컴퓨터에서 이미지, 영상을 표현하는 데 필요한 연산을 수행하는 그래픽 처리 장치이다. 모니터에 출력되는 화면, 3D graphics, 특수 효과는 대규모 **Vector·Matrix Operation**과 **Parallel Processing(병렬 연산)** 을 거쳐 생성되며, GPU는 이를 고속으로 처리하는 데 최적화된 하드웨어이다.

흔히 GPU라고 하면 그래픽카드와 같은 의미로 사용하는 경우가 많지만, 엄밀히 말하면 둘은 명확 구분되는 개념이다.

- **GPU:** 연산을 수행하는 반도체 칩
- **그래픽카드:** GPU에 그래픽 메모리, 전원 공급 회로, 냉각장치 등을 결합한 하드웨어 장치


![NVIDIA AD102 GPU](https://github.com/user-attachments/assets/7c68ab99-284c-4186-85dc-2f0c2e4ecde1)

*그림 1. NVIDIA GeForce RTX 4090에 사용되는 AD102 GPU chip*

---

![ASUS ROG Strix GeForce RTX 4090 그래픽카드](https://upload.wikimedia.org/wikipedia/commons/7/76/Asus_Strix_RTX_4090.jpg)

*그림 2. ASUS ROG Strix GeForce RTX 4090 그래픽카드*

## 2. GPU VS CPU

CPU는 컴퓨터의 전반적인 동작을 제어하고 명령어를 처리하는 하드웨어이다.

반면 GPU는 수천 개의 Core(연산 장치)를 활용해 대규모 데이터에 동일한 연산을 동시에 적용하는 Parallel Processing에 특화되어 있다. 단, 전체 Throughput(처리량)이 높다고 해서 모든 작업에서 CPU보다 빠른 것은 아니다. Sequential Processing(순차 작업)이나 복잡한 Branching(조건 분기)이 많은 작업에서는 GPU의 효율이 떨어진다.

![CPU vs GPU Architecture](https://upload.wikimedia.org/wikipedia/commons/c/c6/Cpu-gpu.svg)

*그림 3. CPU와 GPU의 내부 구조 비교 (초록색 ALU가 연산 장치)*

---

| 구분 | CPU | GPU |
|---|---|---|
| 설계의 중점 | 명령어 처리 및 제어 | 많은 연산을 병렬로 처리 |
| 특화된 작업 | 순차적인 작업, 조건 분기 | 행렬 및 벡터의 연산 |
| 활용 | OS, 응용 프로그램 실행 | 그래픽 렌더링, 인공지능 연산 |


> CPU와 GPU는 각기 다른 영역에 특화되어 있어 상호 보완적으로 작동하는 하드웨어이다.

## 3. GPU가 화면을 만드는 과정

3차원 공간의 데이터를 바탕으로 2차원 화면 이미지를 생성하는 과정을 Rendering이라 한다. 3차원 물체는 Vertex(정점)와 Polygon(다각형) 같은 기하학적 정보로 표현된다. GPU는 이러한 정보에 물체의 위치와 관찰 방향을 반영하고 화면에 표시할 색상(RGB 등)을 계산한다.

다음과 같이 순서를 간단하게 나타낼 수 있다.

1. **위치 및 시점 변환 (Vertex Processing):** 3차원 공간에서 물체의 위치와 카메라 시점을 계산
2. **화면 투영 (Rasterization):** 3차원 물체가 2차원 화면의 어느 Pixel에 위치하는지 변환
3. **색상 계산 (Pixel Shading):** 표면 재질(Texture)과 조명(Lighting)을 반영해 최종 색상 결정
4. **화면 출력 (Frame Buffering):** 계산된 결과를 결합해 하나의 완성된 이미지 생성

여기에서 설명하는 하나의 이미지를 **프레임(Frame)** 이라 하며 시각적으로 움직이는 장면을 만들기 위해 새로운 이미지를 계속해서 만들어야 한다. 초당 프레임 수를 **FPS(Frames Per Second)** 라고 한다.

## 4. VRAM의 역할

GPU가 연산을 하기 위해서는 피연산자 즉, 데이터를 저장할 메모리가 필요하다. 외장 그래픽카드에는 이러한 데이터를 저장하는 **VRAM** 이라는 전용 그래픽 메모리가 탑재된다. VRAM에는 일반적으로 다음 데이터가 저장된다.

- 물체 표현의 질감을 표현하는 **Texture** 데이터
- 물체의 형태와 공간의 좌표를 담고 있는 **Vertex** 데이터
- 화면에 출력할 최종 **Frame Buffer** 및 연산 중간 결과 데이터

## 5. 정리

- **GPU**는 대규모 **Vector·Matrix Operation**을 동시에 처리하는 **Parallel Processing** 특화 반도체 칩이며, 이를 구동하기 위해 **VRAM**, 전원부, 쿨러 등을 결합한 장치가 **그래픽카드**이다.
- **CPU**는 복잡한 제어와 순차 작업(**Sequential Processing**)을 담당하고, **GPU**는 대규모 반복 연산을 분담하여 상호 보완적으로 동작한다.
- GPU는 3차원 데이터를 2차원 화면으로 변환하는 **Rendering** 과정을 초당 수십~수백 번(**FPS**) 반복하여 움직이는 화면을 출력하며, 이 과정에서 필요한 대용량 데이터는 전용 메모리인 **VRAM**에 상주한다.

**이미지 출처**
- 그림 1: Fritzchens Fritz, Wikimedia Commons (CC0 1.0)
- 그림 2: Benlisquare, Wikimedia Commons (CC BY-SA 4.0)
- 그림 3: Offnfopt, Wikimedia Commons (CC BY-SA 4.0)
