---
description: 다음은 기본 모바일 지표 및 차원에 대한 참조 정보입니다.
keywords: mobile
seo-description: 다음은 기본 모바일 지표 및 차원에 대한 참조 정보입니다.
seo-title: 모바일 지표 및 차원 참조
solution: Marketing Cloud, Analytics
title: 모바일 지표 및 차원 참조
topic: 지표
uuid: 96170 AE 7-8553-4 F 3 E-AE 01-65 E 5 B 664 ADF 4
translation-type: tm+mt
source-git-commit: 056bb3edb94c2ceb2961bbe8e4851c20429e1ea2

---


# Mobile metrics and dimensions reference {#mobile-metrics-and-dimensions-reference}

이 정보는 기본 모바일 지표 및 차원에 대한 자세한 내용을 이해하는 데 도움이 됩니다.

>[!TIP]
>
>Adobe Analytics에 설정된 차원 및 지표 권한은 Mobile Services에 적용됩니다. 적절한 권한 없이 보고서를 실행하려고 하면 오류가 발생합니다.

## 지표 {#section_6704C815147D44AF96151D626BEB813C}

다음은 기본 모바일 지표 목록입니다.

* **첫 번째 실행**

   설치 또는 재설치 후 첫 번째 실행에서 트리거됩니다.

* **업그레이드**

   업그레이드 후 첫 번째 실행에서 또는 버전 번호가 변경될 때 트리거됩니다.

* **일별 참여 사용자**

   특정 날짜에 애플리케이션을 사용할 때 트리거됩니다.

   >[!TIP]
   >일별 참여 사용자 이벤트는 Analytics 지표에 자동으로 저장되지 않습니다. 이 지표를 캡처하려면 사용자 지정 이벤트를 설정하는 처리 규칙을 만들어야 합니다.

* **월별 참여 사용자**

   특정 월에 응용 프로그램을 사용할 때 트리거됩니다.

   >[!TIP]
   >월별 참여 사용자 이벤트는 Analytics 지표에 자동으로 저장되지 않습니다. 이 지표를 캡처하려면 사용자 지정 이벤트를 설정하는 처리 규칙을 만들어야 합니다.

* **시작**

   설치 또는 업그레이드가 아닌 실행 시 트리거됩니다. 응용 프로그램이 백그라운드에서 나올 때도 트리거됩니다. 기본적으로 새 시작은 응용 프로그램이 5분 이상 백그라운드에 있을 경우 트리거됩니다. The amount of background time before triggering a new launch can be configured in **[!UICONTROL SDK Analytics Options]** on the Manage App Settings page. 자세한 내용은 SDK 분석 옵션 구성에서 *세션 시간 초과 (초)* [행을 참조하십시오](/help/using/c-manage-app-settings/c-mob-confg-app/t-config-analytics/t-config-analytics.md).

   >[!IMPORTANT]
   >Because how visits in [!UICONTROL Adobe Analytics] and mobile app launches in [!UICONTROL Adobe Mobile Services] are calculated, you might see different results in reporting. 자세한 내용은 [방문 및 모바일 앱 실행 비교](https://helpx.adobe.com/analytics/kb/compare-visits-and-mobile-app-launches.html)를 참조하십시오.

* **충돌**

   응용 프로그램이 올바르게 종료되지 않을 때 트리거됩니다. 이 이벤트는 응용 프로그램이 충돌 후에 시작될 때 전송됩니다.

   >[!TIP]
   >종료가 호출되지 않으면 애플리케이션이 충돌으로 간주됩니다.

* **총 세션 길이**

   총 세션 길이를 집계한 것입니다.

## 차원 {#section_1784C7E859F64CCEB95C5DD1DCF5C98D}

다음은 기본 모바일 차원 목록입니다.

* **설치 날짜**

   설치 후 처음 시작하는 날짜. 이 날짜는 *MM/DD/YYYY* 형식입니다.

* **앱 ID**

   애플리케이션 이름과 버전을 다음 형식으로 저장: `[AppName] [BundleVersion]`. 예, `myapp 1.1`.

* **시작 번호**

   응용 프로그램을 시작하거나 백그라운드에서 나온 횟수입니다.

* **최초 사용 이후 일 수**

   처음 실행한 이후 일 수.

* **마지막 사용 이후 일 수**

   마지막 사용한 이후 일 수.

* **시간**

   앱이 실행된 시간을 측정하고 24시간 숫자 형식을 사용합니다. 이 차원은 피크 사용 시간을 판별하기 위해 시간에도 사용됩니다.

* **요일**

   앱을 시작한 평일 횟수.

* **운영 체제**

   장치의 운영 체제.

* **운영 체제 버전**

   운영 체제 버전.

* **마지막 업그레이드 이후 일 수**

   애플리케이션 버전 번호가 변경된 이후의 일수입니다.

   >[!TIP]
   >
   >마지막 업그레이드 이후 일 수는 Analytics 변수에 자동으로 저장되지 않습니다. 보고를 위해 이 값을 Analytics 변수에 복사하려면 처리 규칙을 생성해야 합니다.

* **마지막 업그레이드 이후 출시**

   애플리케이션 버전 번호가 변경된 이후의 시작 횟수.

   >[!TIP]
   >
   >마지막 업그레이드 이후 론치는 Analytics 변수에 자동으로 저장되지 않습니다. 보고를 위해 이 값을 Analytics 변수에 복사하려면 처리 규칙을 생성해야 합니다.

* **장치 이름**

   장치 이름을 저장합니다. iOS에서 쉼표로 구분된 두 자리 문자열은 iOS 장치를 식별합니다. 첫 번째 숫자는 장치 생성을 나타내고 두 번째 번호는 장치 제품군의 다른 구성원을 나타냅니다. 일반적인 장치 이름의 전체 목록에 대해서는 [iOS 장치 버전](/help/ios/reference/device-versions.md)을 참조하십시오.

* **통신사 이름**

   모바일 서비스 공급자의 이름을 저장합니다.

* **해상도**

   너비와 높이(실제 픽셀).