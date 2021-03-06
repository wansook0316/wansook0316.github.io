---
layout: post
title: "06: 통계 기법 이해"
category: "DS/ML"
comments: true
tags: [Data Science, "Machine Learning", "빅데이터분석기사"]
feature-img: "assets/img/77.jpg"
feature-title: ""
use_math: true
summary: "기술통계와 추론통계에 대해 알아본다."
series: "빅데이터분석기사 - 필기"
---


# 기술 통계 (Desciptive Statistics)

* 확률 통계적으로 정리 및 요약
* 평균
* 중위수
* 최빈수
* 범위
* 분산
* 표준편차
* 표준오차
* 분포
  * 첨도
  * 왜도
* 상관분석
  * 피어슨 상관계수 - 수치 변수
  * 카이제곱 검정 - 명목 변수
  * 스피어만 순위상관계수 - 순서 변수
* 회귀 분석
  * 설명력 - $R^2$
  * 전제조건
    * 선형성
    * 등분산성
    * 독립성
    * 비상관성
    * 정규성
  * 변수선택 방법
    * 전진
    * 후진
    * 단계
* 분산 분석(ANOVA)
  * 집단간 비교를 수행
  * F 분포를 이용하여 가설 검정 - 집단 내 분산 대비 집단 간 분산의 크기를 나타내는 값
  * 일원 분산 분석
    * 독립변수 1개, 종속변수 1개
  * 이원 분산 분석
    * 독립변수 2개, 종속변수 1개
  * 다변량 분산 분석
    * 종속변수 2개 이상
  * 공분산 분석
* 주성분 분석(PCA)
  * 원래 변수보다 적은 수의 주성분을 통해 해석
* 다변량 기법


# 표본 추출

* 단순 무작위 추출
  * 규칙없이 표본 추출
  * 100개의 전구에서 무작위로 10개 추출
* 계통 추출
  * 일정한 간격으로 추출
  * 100명 사람에게 번호표 주고, 끝자리 7인 사람들 선정
* 층화 추출
  * 계층으로 나누고, 그 계측에서 무작위 추출
  * 계층은 내부적으로 동질적, 외부적으로 이질적
  * 여론 조사에 있어 조사 지역을 도별로 나누고, 각 도에서 100명씩 무작위 선정
* 군집 추출
  * 여러 군집으로 나누고 추출
  * **군집 성질 고려하지 않음**
  * **간격도 중요하지 않음**
  * 100개 전구에 무작위로 RGB 칠하고 파란색 모두 추출


# 확률 분포

* 이산확률분포
  * 포아송 분포 - 특정 시간동안 일어나는 사건의 수
  * 베르누이 분포
  * 이항 분포
* 연속확률분포
  * 정규분포
  * 표준정규분포
  * t-분포
    * 평균의 해석에 사용
    * 모집단은 정규 분포, 모표준편차는 모름
    * 30이하의 개수에 대해서 사용
  * 카이제곱 분포
  * F-분포

# 표본 분포

![image](https://user-images.githubusercontent.com/37871541/114738703-2e6b6980-9d83-11eb-8374-28f5bc17b534.png){: .center-verysmall}

모집단에서 추출된 표본을 관찰하여 나온 통계량을 기반으로 모집단에서 관찰하고 싶은 모수를 추정한다.

* 모집단
* 모수(parameter)
* 통계량
* 추정량
* 표준편차
* 표준오차 - 통계량의 변동 정도


## 표본 조사

표본을 모집단에서 뽑는 과정을 말한다.

* 표본오차
  * 추출한 표본이 모집단을 대변하지 못하여 발생하는 오차
* 비표본오차
  * 조사 과정에서 발생하는 오차
* 표본편의
  * 표본이 가지는 통계량이 모수에 비해 치우친 정도

## 표본 분포 관련 법칙

* 큰수의 법칙
  * 데이터를 많이 뽑으면 표본평균의 분산은 0에 가까워짐
* 중심 극한 정리
  * 표본의 개수가 커지면, 모집단 분포와 상관없이 표본평균의 분포는 정규분포에 근사


## 표본 분포 유형

* Z-분포
* T-분포
* 카이제곱 분포
* F-분포 - 분산의 비율


# 추론 통계

추정을 통해 모집단을 이해하려는 시도

## 점추정

* 불편성
* 효율성
* 일치성
* 충족성

## 구간 추정

* 신뢰수준
* 신뢰구간

# 가설 검정

* 귀무가설 - 기존의 통념
* 대립가설 - 내가 증명하고 싶은 가설

p-값과 유의 수준을 비교하여 귀무 가설 또는 대립 가설을 채택한다.

## 검정 종류

* 양측 검정
  * 같다, 아니다로 검증
* 단측 검정
  * 모수를 기준으로 (작다, 아니다), (크다, 아니다)와 같이 귀무 가설과 대립 가설을 설정한다.

## 오류 종류

* 제 1종 오류
  * 귀무 가설이 실제로 맞으나, 대립 가설을 채택한 경우
* 제 2종 오류
  * 대립 가설이 실제로 맞으나, 대립 가설을 기각한 경우

## 용어 종류

![image](https://user-images.githubusercontent.com/37871541/115005116-8371c180-9ee2-11eb-882a-3c12b1fb77b2.png){: .center-small}

* 왼쪽부터 순서대로
* 신뢰수준 - $(1-\alpha)$
* 유의수준 - $\alpha$
* 베타수준 - $\beta$
* 검정력 - $(1-\beta)$