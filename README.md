# 🌦️ 다중 기상 예보 앙상블 기반 기온 예측 오차 최소화 연구

기상청, 아큐웨더, 메테오블 등 다중 기상 예보 채널의 단일 예측 온도 데이터를 통합 수집하고, 선형 회귀(Linear Regression) 가중치 매핑 및 의사결정나무 기반 앙상블(Ensemble) 모델을 활용하여 내일 및 모레의 실제 관측 온도 오차(RMSE, MAE)를 유의미하게 보정한 학술 연구 프로젝트입니다.

---

## 📂 프로젝트 구조

* **[[붙임] 다중 기상 예보 데이터의 선형 회귀 및 앙상블 기법을 활용한 기온 예측 오차 최소화 연구.pdf](file:///c:/Users/5174k/Code/202210822/%5B%EB%B6%99%EC%9E%84%5D%20%EB%8B%A4%EC%A4%91%20%EA%B8%B0%EC%83%81%20%EC%98%88%EB%B3%B4%20%EB%8D%B0%EC%9D%B4%ED%84%B0%EC%9D%98%20%EC%84%A0%ED%98%95%20%ED%9A%8C%EA%B7%A0%20%EB%B0%8F%20%EC%95%94%EC%83%81%E1%86%B8%20%EA%B8%B0%EB%B2%95%EC%9D%84%20%ED%99%9C%EC%9A%A9%ED%95%9C%20%EA%B8%B0%EC%98%A8%20%EC%98%88%EC%B8%A1%20%EC%98%A4%EC%B0%A8%20%EC%B5%9C%EC%86%8C%ED%99%94%20%EC%97%B0%EA%B5%AC.pdf)**: 학술 연구 최종 논문 보고서
* **[진짜스터디상생.ipynb](file:///c:/Users/5174k/Code/202210822/진짜스터디상생.ipynb)**: 다중 소스 데이터 로드, 전처리, 잔차 플롯 드로잉 및 회귀 분석 통합 실험 노트북
* **[temp_prediction_performance.png](file:///c:/Users/5174k/Code/202210822/temp_prediction_performance.png)**: 예측 채널별 실제 기온 대비 오차율 비교 분석 차트
* **[clean_weather_data.csv](file:///c:/Users/5174k/Code/202210822/clean_weather_data.csv)**: 기상청, 웨더채널, 메테오블 등의 원본 예측 시계열 정제 데이터셋
* **[기상청.csv](file:///c:/Users/5174k/Code/202210822/기상청.csv)** / **[아큐웨더.csv](file:///c:/Users/5174k/Code/202210822/아큐웨더.csv)**: 다중 예보 채널 개별 예측값 소스 데이터

---

## ✨ 연구 프로세스 및 모델링

1. **시계열 예측 데이터 정제 및 동기화**
   * 수집 주기가 불규칙하거나 포맷이 다른 7개 예보 서비스의 단기 예측 온도를 날짜/시간축 단위로 정밀 조인(Outer Join) 및 결측치 보간.
2. **채널별 예측 편향(Bias) 산출**
   * 단일 기상 예보 서비스들이 갖는 계절별, 시간대별 고유 오차 특성 분석.
3. **가중 선형 회귀(Weighted Linear Regression) 모델**
   * 각 예보 채널의 과거 예측 기여도(신뢰 지표)를 가중치 파라미터 $\beta_i$로 산정하여 수학적 최적 기온 보정식 수립.
4. **앙상블(Ensemble) 트리 모델 적용**
   * 온도 변화의 비선형적인 패턴(기압, 풍향, 습도 변동 등)을 포착하기 위해 **의사결정 트리 및 앙상블 기계학습 모델**을 학습시켜 추가 보정.
5. **예측 오차 최소화 성과**
   * 기존 기상청 단독 예보 대비, 다중 채널 보정 융합 모델 적용 시 **RMSE(평균 제곱근 오차) 기준 최대 15% 이상의 오차 개선** 달성.

---

## 🛠️ 기술 스택

* **Language**: `Python`
* **Data Science**: `Pandas`, `Numpy`, `Scikit-learn` (Linear Regression, Regressor Ensembles)
* **Visualization**: `Matplotlib`, `Seaborn` (잔차 플롯, 오차 곡선, 온도 오프셋 시각화)
