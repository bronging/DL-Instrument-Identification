# Deep Learning-Based Instrument Identification in Orchestra Performances

![KCC포스터](https://github.com/user-attachments/assets/373c2eb5-84d0-4b13-8520-4377e413387c)
###### *📰 한국정보과학회 KCC2024 학부생 논문 포스터*


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

## 데이터셋


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

-`전체 시스템 구조`:  특정 한 악기가 입력 데이터 내에 존재하는지 아닌지를 출력하는 CNN 모델로 이루어진 악기 식별기 16개로 구성되었습니다.

![DL_Model.drawio.png](README%20df1a6753b5f04bd78631652bc964fd25/DL_Model.drawio.png)

-`악기식별기 구조` 

*TensorFlow*의 *Keras* 라이브러리를 사용하여 모델 생성 및 훈련을 진행했습니다.

![Untitled](README%20df1a6753b5f04bd78631652bc964fd25/Untitled.png)



### 참조문헌

[1] Babak Toghiani-Rizi, Musical Instrument Recognition Using Their Distinctive Characteristics in Artificial Neural Networks, 2017
