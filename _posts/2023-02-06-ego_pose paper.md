---
title: '[Paper Review] Estimating Egocentric 3D Human Pose in the Wild with External Weak Supervision'
date: 2023-02-6 00:00:01
categories:
- Paper Review
tags: PoseEstimation Egocentric Reconstruction 
comments: true
use_math: true
---


[Paper Review] [Estimating Egocentric 3D Human Pose in the Wild with External Weak Supervision](https://openaccess.thecvf.com/content/CVPR2022/papers/Wang_Estimating_Egocentric_3D_Human_Pose_in_the_Wild_With_External_CVPR_2022_paper.pdf)

<!-- more -->

# Abstract
- 하나의 fisheye 카메라를 이용한 **자기 중심 3D 인간 포즈 추정**이 최근 상당한 관심
- 기존 방식은 합성 데이터에서만 훈련할 수 있고, 신체 부위가 주변 장면에 의해 가려지거나 상호 작용할 때 실제 이미지의 포즈 추정이 **어려움**
- Egocentric Poses in the Wild(**EgoPW**)는 **자기 중심 카메라와 외부 카메라**로 촬영한 데이터 동기화
- **weak external supervision**으로 새로운 자기 중심적 자세 추정 방법 제시 : 1) 외부 뷰 감독을 통합하여 **시공간 최적화 방법**으로 EgoPW 데이터 세트에 대한 **pseudo label** 생성 2) pseudo label로 자기 중심 포즈 추정 네트워크 훈련
- 사전 학습된 **외부 뷰 포즈 추정 모델**로 추출한 고품질 feature로 **자기 중심적** feature를 감독하는 새로운 학습 전략 제안
- 단일 자기 중심 이미지에서 정확한 3D 포즈를 예측하고 양적, 질적으로 최첨단 방법 **능가**

# Introduction
- 기존 모션 캡처 시스템은 넓은 공간에서는 적용 범위가 **제한적**이므로, 자기중심적인 모션 캡처 이용
    - 자기중심적 모션 캡처 시스템은 이동성이 유연하며 기록 공간 요구 사항 없음
    - 웨어러블 의료 모니터링, 스포츠 분석 및 $x$R과 같은 많은 애플리케이션에 대한 광범위한 인간 활동 캡처 가능
- 본 연구는 단일 머리 장착 fisheye 카메라에서 전체 3D 신체 포즈를 추정하는 데 중점
    - 가장 관련성이 높은 작업은 Mo$^2$Cap$^2$과 $x$R-egoose
    - 기존 방법은  합성 이미지에 대해서만 훈련되므로 실제 시나리오에서 상당한 성능 저하
    - 인체의 일부가 주변 장면에 의해 가려지거나 상호작용하는 경우 어려움 → 합성 데이터와 실제 데이터 사이의 도메인 격차 및 가림을 처리하는 능력의 제한 때문