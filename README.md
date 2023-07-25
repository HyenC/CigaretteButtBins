# 🚬 마포구 최적의 꽁초 쓰레기통 입지 추천
## 1️⃣ 개요
세계보건기구(WTO)는 전 세계 담배 판매량의 3분의 2가 땅바닥에 버려지는 것으로 추산한다. 꽁초는 무단 투기되었을 경우, 화재, 해양 오염, 토양 오염에 영향을 미친다.
적절한 위치에 담배꽁초 전용 쓰레기통을 설치하여 투기를 줄이고, 환경오염 감소 효과를 기대한다.
<div>
  <img width="400" alt="image" margin='auto 'src="https://github.com/HyenC/CigaretteButtBins/assets/38906574/ad9e2b9e-6bdf-4ed4-b93e-85e62efe284b">
  <img width="400" alt="image" src="https://github.com/HyenC/CigaretteButtBins/assets/38906574/8c682731-d608-4ec1-89c5-efa1ebda09f7">
</div>

## 2️⃣ 분석 내용
- 쓰레기통 위치에 영향을 미치는 요인으로 투기지역, 흡연구역, 담배소매인, 상권, 생활인구를 비교했다. 그 중 흡연구역, 투기지역, 담배소매인, 상권이 쓰레기통 입지에 영향을 미칠 수 있는 요인으로 파악된다.

### 1. 쓰레기통 위치에 영향을 미치는 요인 파악(지도 시각화)
#### 1-1. 투기지역, 흡연구역
투기지역과 흡연구역이 근접한 경향을 보임을 발견하였다. 🔴담배꽁초 투기지역, 흡연구역(🔵실외, 🟡실내)
<img width="744" alt="image" src="https://github.com/HyenC/CigaretteButtBins/assets/38906574/8d0c87ba-f4fc-4739-88a9-66b78b15eba3">

#### 1-2. 흡연구역, 담배소매인
흡연구역과 담배 소매인의 위치값이 일치하거나 유사한 경향을 보임을 발견하였다. 🔵흡연구역, 🔴담배소매인
<img width="743" alt="image" src="https://github.com/HyenC/CigaretteButtBins/assets/38906574/c679f993-6e3c-4a36-920f-3648320ed716">
</br>
흡연구역, 담배소매인 일치 정도(🟣진할수록 일치)
<img width="743" alt="image" src="https://github.com/HyenC/CigaretteButtBins/assets/38906574/4ab40502-7156-4afa-b25f-438aec7f8dad">

#### 1-3. 상권, 생활인구 - 쓰레기통
<img width="640" alt="image" src="https://github.com/HyenC/CigaretteButtBins/assets/38906574/9573b71f-2ce0-4051-8077-140660a9e0e8">

- 상권과 쓰레기통 개수를 시각화하여 비교한 것이다. 두 변수를 상관분석 했을 때 연관성은 0.71이다. 쓰레기통이 설치된 위치는 주변 상권 수와 관련이 있으므로, 추후 쓰레기통 입지 분석에서는 상권을 고려할 수 있다.
- 쓰레기통수 상위 3 : 영등포구 > 마포구 > 서초구
- 상권수 상위 3 : 강남구 > 영등포구 > 서초구

</br>

<img width="640" alt="image" src="https://github.com/HyenC/CigaretteButtBins/assets/38906574/fd188fe3-907e-4a84-8e80-6ed92badc867">

- 시군구별로 평균을 낸 생활인구과 쓰레기통 위치를 시각화하여 비교한 것이다. 두 변수를 상관분석 했을 때 연관성은 0.15이다. 쓰레기통이 설치된 위치는 평균 생활인구 수와는 관련이 없어 보이므로, 추후 쓰레기통 입지 분석에서는 생활인구를 고려하지 않는다.
- 평균 생활인구 수 상위 7 : 강동구>송파구>관악구>광진구>은평구>강서구>중랑구
- 쓰레기통수 상위 7 : 영등포구>마포구>서초구>강남구>종로구>동작구>양천구>중랑구

### 2. 쓰레기통 위치 추천 모델링을 위한 마포구 선정 이유
- 아래 표에 따르면 흡연구역 대비 쓰레기통 개수가 부족한 시군구가 존재한다.
- 중랑구는 0.03으로 흡연구역 대비 쓰레기통 수가 가장 낮은 비율을 보이지만, 마포구는 담배 관련 데이터의 양이 많다. ex) 중랑구 쓰레기통=7개, 마포구 쓰레기통=65개
- 마포구의 쓰레기통 데이터셋은 일부 지역에 한정되어 있기 때문에 마포구 전체를 대상으로 새로운 쓰레기통 위치 추천에 용이할 것으로 판단하였다.
<img width="537" alt="image" src="https://github.com/HyenC/CigaretteButtBins/assets/38906574/aaccfedb-4c52-4116-b45e-0269794db669">

### 3. 쓰레기통 위치 추천 모델링
- 위치 추천 모델링의 방법으로는 군집 분석을 활용한다. 앞서 분석한 내용을 토대로 모델링의 변수로는 흡연구역과 투기지역, 담배소매인, 상권을 적절하게 활용한다.
#### 3-1. 계층적 군집 분석
- 계층적 군집 분석은 가까운 대상부터 결합하여 군집을 형성하는 방법이다.
<img width="662" alt="image" src="https://github.com/HyenC/CigaretteButtBins/assets/38906574/f8f486fd-32b1-4989-b480-cafe613148da">

- 유클리디안 거리를 이용한 추천
- 유클리디안은 두 점 사이의 거리를 계산하여 군집화하는 대표적인 방법이다. 중랑구, 영등포구, 양천구의 유사도를 적용하고 흡연구역과 투기지역을 변수로 활용하여 마포구의 쓰레기통 추천 위치를 도출했다.

</br>

<img width="689" alt="image" src="https://github.com/HyenC/CigaretteButtBins/assets/38906574/302e948c-2391-4c85-a94d-28c5a41b8b71">

- 하버사인 거리를 이용한 컨텐츠 기반 필터링
- 중랑구, 영등포구, 양천구의 유사도를 적용하고, 흡연구역과 투기지역을 변수로 활용하여 마포구의 쓰레기통 추천 위치를 도출했다. 유클리디안과 결과가 동일하지만 다른구의 쓰레기통 위치까지 표시된다.

#### 3-2. 비계층적 군집 분석
- 비계층적 군집 분석은 군집 수를 정한 상태에서 가까운 개체부터 포함해 나간다. 계층적 군집으로 군집의 수를 파악하고, 초기 군집 수로 설정하여 비계층적 군집 분석을 수행하는 방법이 일반적이다.

<img width="575" alt="image" src="https://github.com/HyenC/CigaretteButtBins/assets/38906574/7ff4c8a4-6803-466d-9968-fed6facad6e7">

- K-means Clustering
- K-means Clustering은 대표적인 비계층적 군집 분석 방법이다. 엘보우 그래프를 통해 본 최적 군집의 수는 기울기가 가장 가파른 2개이다. 하지만, 해당 프로젝트는 각 구역 특성을 고려하여 적절하게 추천하고자 하므로, 군집 개수를 임의로 지정했다.

<div>
  <img width="500" alt="image" src="https://github.com/HyenC/CigaretteButtBins/assets/38906574/9caa7de2-fb18-4faf-a294-b16879380591">
  <img width="500" alt="image" src="https://github.com/HyenC/CigaretteButtBins/assets/38906574/20c28543-3938-4557-b966-106ba0310898">
</div>

</br>

- 군집의 개수를 정할 때, 너무 적으면 다양성을 보여주기 어렵고, 너무 많으면 과적합이 될 수 있으므로 도메인 지식을 활용하기도 한다. 마포구는 현재 26개의 법정동으로 구분되어 있는 것에 착안하여 군집수를 26으로 설정한다. 26으로 설정 시, 쓰레기통 추천 위치와 군집 분포는 다음과 같다.

<div>
  <img width="500" alt="image" src="https://github.com/HyenC/CigaretteButtBins/assets/38906574/75f9e980-3615-47e8-a228-c099126b27cb">
  <img width="500" alt="image" src="https://github.com/HyenC/CigaretteButtBins/assets/38906574/f68c7e8a-bb83-437e-a496-c093365011d1">
</div>

## 3️⃣ 결론

> 쓰레기통 위치 추천 모델링 시, 계층적 군집분석으로 유클리디안과 하버사인 거리를 활용하였고, 비계층적 군집분석으로 K-means clustering을 활용하였다. 계층적 군집분석에서는 프로젝트에서 목표하던 흡연구역 대비 쓰레기통 비율을 1에 가깝게 끌어올릴만큼의 개수가 추천되지 않았으므로 군집의 개수만 참고하고 K-means clustering을 활용한 모델을 최종적으로 사용하여 쓰레기통 입지 추천을 한다.
