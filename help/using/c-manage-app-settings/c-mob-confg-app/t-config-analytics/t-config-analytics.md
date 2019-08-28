---
description: 새 앱을 만들거나 기존 앱을 편집하는 동안 [앱 설정 관리] 페이지에서 SDK Analytics 옵션을 구성할 수 있습니다.
keywords: mobile
seo-description: 새 앱을 만들거나 기존 앱을 편집하는 동안 [앱 설정 관리] 페이지에서 SDK Analytics 옵션을 구성할 수 있습니다.
seo-title: SDK Analytics 옵션 구성
solution: Marketing Cloud, Analytics
title: SDK Analytics 옵션 구성
topic: 지표
uuid: FD 3 A 21 D 2-6560-4 E 96-92 FE-B 99 CAAC 5 E 834
translation-type: tm+mt
source-git-commit: d028fe0f9477bc011aa8fda21a0a389808df0fce

---


# Configure SDK Analytics options {#configure-sdk-analytics-options}

새 앱을 만들거나 기존 앱을 편집하는 동안 [앱 설정 관리] 페이지에서 SDK Analytics 옵션을 구성할 수 있습니다.

Type information in the following fields under **[!UICONTROL SDK Analytics Options]**:

* **[!UICONTROL HTTPS 사용]**

   보안 강화를 위해 HTTPS를 활성화합니다.

* **[!UICONTROL 세션 히트 소급 적용]**

   세션 정보 히트를 소급 적용하는 Adobe SDK의 기능을 활성화하거나 비활성화합니다. 세션 정보 히트는 현재 충돌과 세션 길이로 구성됩니다. 활성화되면, Adobe SDK에서는 세션 정보 히트를 이전 세션의 마지막 히트 다음 1초로 소급 적용합니다. 이는 충돌과 세션 데이터가 충돌과 세션이 발생한 올바른 날짜와 상관 관계를 갖게 됨을 의미합니다. 애플리케이션을 매번 새로 시작할 때마다 하나의 히트가 소급 적용됩니다. 비활성화하면, Adobe SDK에서는 현재 라이프사이클에 세션 정보를 추가합니다.

* **[!UICONTROL 개인 정보 보호]**

   개인 정보 옵션을 선택하십시오.

   * **[!UICONTROL 옵트아웃까지 데이터 전송]**
   * **[!UICONTROL 옵트인까지 데이터 일시 중단]**

* **[!UICONTROL 세션 시간 초과(초)]**

   세션 시간 초과 값을 지정합니다.

   기본값은 300초입니다. 앱 시작이 새 세션으로 간주되기 전에 다음 앱이 시작되기까지 경과되어야 하는 시간(초)을 지정합니다. 이 시간 초과는 응용 프로그램이 백그라운드로 전송되고 다시 활성화될 때도 적용됩니다. 앱이 백그라운드에서 소요하는 시간은 세션 길이에 포함되지 않습니다.

* **[!UICONTROL 배치 한도]**

   데이터를 보내기 전에 큐에 올릴 히트 수를 지정합니다.

   히트를 즉시 보내려면 0으로 설정하십시오. 배치 한도는 연속적인 호출에서 보내질 히트 수에 대한 임계값을 나타냅니다. 예를 들어, 이 옵션을 10으로 설정하면, 10번째 히트 전에 있는 각 히트가 큐에 저장됩니다. 10번째 히트가 들어오면 10개의 히트가 모두 연속적으로 전송됩니다.

* **[!UICONTROL 더 자세히]**

   보고서 세트 ID와 추적 서버를 보고, 오프라인 추적을 활성화하거나 비활성화하고, 사용할 문자 인코딩 모델(예: UTF-8)을 보려면 **[!UICONTROL 더 자세히]를 클릭하십시오.**

   오프라인 추적이 활성화되면, 오프라인 동안 장치가 생성한 데이터에 타임스탬프가 지정되고 나중에 전송됩니다. 이 옵션을 비활성화하면 오프라인 데이터가 무시됩니다.