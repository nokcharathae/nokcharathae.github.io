---
title: Unreal Engine 5 Niagara System
date: 2022-11-16 00:01:36
categories:
- Unreal Engine 5
tags: UE5 Niagara
comments: true
---


[Unreal Engine 5] 나이아가라 사용법

<!-- more -->

# Niagara System 사용하는 방법

### Global Distance Field
Global Distance Field는 카메라를 따르는 동안 해당 Level에서 Signed Distance Fields occlusion을 사용하는 low-resolution Distance Field입니다. 이것은 객체별 메시 거리 필드의 캐시를 생성하고 클립맵이라고 불리는 카메라를 중심으로 한 몇 가지 볼륨 텍스처로 합성한다. 새로 보이는 영역이나 장면 수정의 영향을 받는 영역만 업데이트하면 되기 때문에 구성 비용이 많이 들지 않는다.

객체 거리 필드의 해상도가 낮다는 것은 모든 것에 사용할 수 있다는 것을 의미하지만 하늘 폐색을 위한 원뿔 추적을 계산할 때 전역 거리 필드가 더 멀리 샘플링되는 동안 음영이 있는 지점 근처에서 샘플링됩니다.

#### Visualize Global Distance Field
뷰포트에서 전역 거리 필드를 시각화기 위해서는 [Show] - [Visualize] - [Global Distance Field]를 체크합니다.

# 참고
* https://www.unrealengine.com/en-US/metahuman?sessionInvalidated=true

