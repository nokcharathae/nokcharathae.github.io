---
title: "[Unreal Engine] Niagara VFX System"
date: 2022-11-16 00:01:36
categories:
- Unreal Engine
tags: UE Niagara
comments: true
---


[Niagara VFX System](https://docs.unrealengine.com/5.0/en-US/creating-visual-effects-in-niagara-for-unreal-engine/){:target="_blank"}관련 Unreal Engine Documentation을 참고하여 작성되었습니다. Unreal Engine의 Niagara VFX System을 사용하여 파티클 효과를 실시간으로 생성하는 방법을 서술합니다. 본 내용은 UE4와 UE5의 Niagara Documentation을 혼합하여 작성되었습니다. 

<!-- more -->

# Niagara System 
## [Niagara Overview](https://docs.unrealengine.com/5.0/en-US/overview-of-niagara-effects-for-unreal-engine/){:target="_blank"}
Niagara는 Unreal Engine의 차세대 VFX 시스템입니다.

### Core Niagara Components
* [Systems](#systems)
* [Emitters](#emitters)
* [Modules](#modules)
* [Parameters](#parameters)


#### Systems
Niagara system은 효과를 만드는 데 필요한 모든 것을 담는 용기입니다. 즉, 하나의 이펙트로 결합된 여러 Emitter의 컨테이너입니다. 시스템 내부에는 전체적인 효과를 생성하는 데 도움이 되는 다양한 빌딩 블록이 쌓일 수 있습니다. Niagara system editor에서 시스템에 있는 이미터 또는 모듈의 모든 항목을 수정하거나 덮어쓸 수 있습니다.
<p align="center"><img src="/assets/images/Image_UE5/01-niagara-system.webp" width="300" height="300" /> </p>

#### Emitters
Emitter는 Niagara system에서 입자가 생성되는 곳입니다. 입자가 어떻게 태어나고, 나이가 들면서 입자에게 무슨 일이 일어나는지, 그리고 입자가 어떻게 보이고 행동하는지를 조절합니다.  
Emitter는 스택으로 구성되고 그 내부에는 여러 그룹이 있으며, 안에 개별 작업을 수행하는 모듈을 넣을 수 있습니다.
<p align="center"><img src="/assets/images/Image_UE5/02-emitters-with-groups.webp" width="300" height="300" /> </p>
1. Emitter Spawn  
이 그룹은 CPU에 이미터가 처음 생성될 때 발생하는 동작을 정의합니다. 이 그룹을 사용하여 초기 설정 및 기본값을 정의합니다.
2. Emitter Update  
이 그룹은 CPU의 모든 프레임에서 발생하는 이미터 수준 모듈을 정의합니다. 이 그룹을 사용하여 모든 프레임에서 입자를 계속 산란시킬 때 입자의 산란을 정의합니다.
3. Particle Spawn  
이 그룹은 입자가 처음 태어날 때 입자당 한 번이라고 불립니다. 여기서 입자가 태어난 위치, 색상, 크기 등 입자의 초기화 세부 정보를 정의할 수 있습니다.
4. Particle Update  
이 그룹은 각 프레임의 입자당 호출됩니다. 입자가 노화됨에 따라 프레임별로 변경해야 하는 모든 것을 여기서 정의할 수 있습니다. 예를 들어, 입자의 색이 시간이 지남에 따라 변하는 경우입니다. 또는 입자가 중력, 컬 노이즈 또는 점 인력과 같은 힘의 영향을 받는 경우. 시간이 지남에 따라 입자의 크기가 변하기를 원할 수도 있습니다.
5. Event Handler  
이벤트 핸들러 그룹에서 특정 데이터를 정의하는 하나 이상의 송신기에 이벤트 생성을 생성할 수 있습니다. 그런 다음 생성된 이벤트에 대한 반응으로 동작을 트리거하는 다른 송신기에서 수신 대기 이벤트를 생성할 수 있습니다.
6.Render  
마지막 그룹은 렌더 그룹입니다. 이 위치에서 파티클의 표시를 정의하고 파티클에 대한 하나 이상의 렌더러를 설정할 수 있습니다. 재료를 적용할 수 있는 3D 모델을 입자의 기초로 정의하려는 경우 Mesh 렌더러를 사용할 수 있습니다. 또는 스프라이트 렌더러를 사용하여 입자를 2D 스프라이트로 정의할 수 있습니다. 선택하고 실험할 수 있는 다양한 렌더러가 있다.


#### Modules

#### Parameters

# 참고
* https://docs.unrealengine.com/5.0/en-US/creating-visual-effects-in-niagara-for-unreal-engine/
* https://docs.unrealengine.com/4.27/en-US/RenderingAndGraphics/Niagara/EmitterEditorReference/
* https://docs.unrealengine.com/4.27/en-US/RenderingAndGraphics/Niagara/Overview/
 