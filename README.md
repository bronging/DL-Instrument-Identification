# Deep Learning-Based Instrument Identification in Orchestra Performances

## **프로젝트 개요**


-`프로젝트 기간` : 23.09.04 ~ 23.12.18

-`프로젝트 내용` : 총 16개 악기에 대해 오케스트라 음원에서 특정 시점에 동시에 연주중인 악기를 식별하는 CNN 모델

## **악기 종류**


<aside>
🎻 
  
**현악기**     바이올린, 비올라, 첼로, 더블베이스

**목관악기**  플룻, 오보에, 클라리넷, 베이스클라리넷, 바순, 색소폰

**금관악기** 트럼펫, 호른, 트럼본, 투바

**타악기**    심벌즈, 탬버린

</aside>

## 데이터


🎷**사용한 데이터셋**

> **URMP Dataset**
mp3 파일, 100MB
> 

[URMP Dataset](https://labsites.rochester.edu/air/projects/URMP.html)

> **Philharmonia Sound samples Dataset**
mp3 파일, 320MB
> 

[Sound samples | Philharmonia](https://philharmonia.co.uk/resources/sound-samples/)

🏋️**훈련 데이터 생성 - Mixed Audio**

주요 오케스트라 악기 16개의 연주 데이터를 각각 4초 단위로 자른 후, 여러 악기의 음원을 합쳐서 총 약 23만 개(15GB)의 데이터를 만들어서 훈련에 사용했습니다. 

## **모델**


-`입력 데이터 타입`: MFCC

*librosa* 라이브러리를 사용해 mixed audio mp3 데이터로부터 MFCC를 추출하여 모델의 입력 데이터로 사용했습니다. 

![mfcc.png](README%20df1a6753b5f04bd78631652bc964fd25/%25EC%258A%25A4%25ED%2581%25AC%25EB%25A6%25B0%25EC%2583%25B7_2024-02-15_21.02.52.png)

-`전체 시스템 구조`:  특정 한 악기가 입력 데이터 내에 존재하는지 아닌지를 출력하는 서브 CNN 모델 16개로 구성되었습니다.

![DL_Model.drawio.png](README%20df1a6753b5f04bd78631652bc964fd25/DL_Model.drawio.png)

-`서브 모델 구조` 

*TensorFlow*의 *Keras* 라이브러리를 사용하여 모델 생성 및 훈련을 진행했습니다.

![Untitled](README%20df1a6753b5f04bd78631652bc964fd25/Untitled.png)

## 결과



-`악기별 모델 정확도` :

|| |||
| --- | --- | --- | --- |
| 바이올린(0.856) | 비올라(0.894) | 첼로(0.908) | 더블베이스(0.925) |
| 플룻(0.837) | 오보에(0.954) | 클라리넷(0.850) | 베이스클라리넷(0.937)) |
| 바순(0.899) | 색소폰(0.811) | 트럼펫(0.806) | 호른(0.786) |
| 트럼본(0.844) | 튜바(0.898) | 심벌즈(0.999) | 템버린(0.999) |


-`전체 모델 정확도` : 

**85.9258%**

### 참조문헌

[1] Babak Toghiani-Rizi, Musical Instrument Recognition Using Their Distinctive Characteristics in Artificial Neural Networks, 2017
