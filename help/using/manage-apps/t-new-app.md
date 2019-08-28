---
description: 이 정보를 사용하여 새 앱 만들기 및 해당 주요 지표 구성, Adobe Analytics 및 Adobe Audience Manager에 대한 SDK 옵션 구성, 획득 및 ID 서비스 옵션 구성, 구성 파일, SDK, 개발자 및 테스터 도구 다운로드 등을 수행할 수 있습니다.
keywords: mobile
seo-description: 이 정보를 사용하여 새 앱 만들기 및 해당 주요 지표 구성, Adobe Analytics 및 Adobe Audience Manager에 대한 SDK 옵션 구성, 획득 및 ID 서비스 옵션 구성, 구성 파일, SDK, 개발자 및 테스터 도구 다운로드 등을 수행할 수 있습니다.
seo-title: 새 앱 추가
solution: Marketing Cloud, Analytics
title: 새 앱 추가
topic: 지표
uuid: 706 B 5 E 4 D -1318-4 A 9 E -8 C 69-FFABF 51 FA 02 C
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# 새 앱 추가{#add-a-new-app}

이 정보를 사용하여 새 앱 만들기 및 해당 주요 지표 구성, Adobe Analytics 및 Adobe Audience Manager에 대한 SDK 옵션 구성, 획득 및 ID 서비스 옵션 구성, 구성 파일, SDK, 개발자 및 테스터 도구 다운로드 등을 수행할 수 있습니다.

이러한 지침은 새 앱을 추가하고 Adobe Analytics 및 Adobe Audience Manager 통합을 구성하는 데 도움이 됩니다.

앱을 구성하려면 먼저 Adobe Mobile Services 사용자 인터페이스에 해당 앱을 추가해야 합니다. 앱을 만든 후에 올바른 구성이 생성되면 앱에 대한 Mobile SDK를 구현하는 개발자에게 이 구성을 제공할 수 있습니다.

1. Adobe Mobile Services에 로그인하고 다음 작업 중 하나를 완료합니다. 

   * **[!UICONTROL 새로 만들기]를 클릭하여 앱을 만듭니다.**
   * To add additional apps, click Manage Apps in the left navigation menu and click **[!UICONTROL Add]**.

      로그인에 대한 자세한 내용은 [로그인을](/help/using/gs/gs-signin.md)참조하십시오.

      >[!TIP]
      >
      >기존 앱을 관리하려면 왼쪽 탐색 메뉴에서 앱 관리를 클릭하고 수정할 앱을 클릭합니다. 앱 정보 페이지에서 변경할 수 있습니다.

1. 다음 필드에 정보를 입력하십시오.

   **[!UICONTROL 보고서 세트]**

   Adobe Analytics에서보고 데이터를 수집하고 저장하는 보고서 세트를 지정합니다. 각 앱은 하나의 Analytics 보고서 세트에 연결됩니다. 앱 데이터를 여러 보고서 세트에 전송하는 경우에는 각 보고서 세트에 대한 새 앱을 추가하십시오. 각 앱은 하나의 Analytics 보고서 세트에 연결됩니다. 앱 데이터를 여러 보고서 세트에 전송하는 경우에는 각 보고서 세트에 대한 새 앱을 추가하십시오.

   Adobe Mobile에서 Analytics 관리자 권한이 제공된 경우 Adobe Mobile에서 새 보고서 세트를 만들 수 있습니다. To create a new report suite, select **[!UICONTROL New Report Suite]** and type information into the following fields:

   * **[!UICONTROL 보고서 세트 ID]**

      이 ID는 Adobe Analytics에서 보고서 세트를 고유하게 식별합니다. 회사 접두사가 ID 시작 부분에 자동으로 추가됩니다.

   * **[!UICONTROL 다음에서 설정 복사]**

      변수, 이벤트, 처리 규칙 및 기타 설정은 이 보고서 세트에 있는 것과 동일하게 새 보고서 세트에 설정됩니다. Mobile Services에서 만든 보고서 세트는 사용된 **다음에서 설정 복사** 보고서 세트가 모바일 앱 템플릿이거나 오프라인이 활성화된 보고서 세트를 만들 경우에만 오프라인이 활성화됩니다.(또는 타임스탬프가 지정됩니다.)

   * **[!UICONTROL 시간대]**

      모든 보고 날짜는 이 시간대에 있습니다. 이 설정은 브라우저에서 사용하는 시간대와 가까운 표준 시간대 사용을 시도합니다.

   * **[!UICONTROL 통화]**

      매출액은 이 유형의 통화로 추적되고 보고됩니다.
   >[!TIP]
   >
   >가상 보고 세트 (VRS) 를 사용하려면 [가상 보고서 세트를 참조하십시오](/help/using/manage-apps/c-mob-vrs.md).

   * **[!UICONTROL 아이콘]**

      (**Optional**) To browse to and select an icon for your app, click **[!UICONTROL Icon]**.

   * **[!UICONTROL 이름]**

      (**Optional**) Type a descriptive name for the app. 이 이름은 앱을 신속하게 찾는 데 도움이 되며 의미 있는 이름은 앱의 목적과 설정을 빨리 이해하는 데 도움이 됩니다.

   * **[!UICONTROL 유형]**

      드롭다운 목록에서 유형을 선택합니다. 왼쪽 탐색 메뉴에 표시되는 사용할 수 있는 보고서는 선택하는 앱의 유형에 따라 달라집니다.

      다음은 사용 가능한 유형입니다.

      * **[!UICONTROL 표준]**

         You can leave the **[!UICONTROL Standard}** option selected for most apps.

      * **[!UICONTROL 발행]**

         앱이 Adobe Digital Publishing Suite를 사용하여 빌드된 경우 이 옵션을 선택할 수 있습니다.

      * **[!UICONTROL 게임]**

         이 옵션은 ****&#x200B;게임]이 보고서에서 사용된 용어를 게임 용어로 업데이트한다는 것을 제외하고, **[!UICONTROL 표준]옵션과 비슷합니다.[!UICONTROL ** 예를 들어 사용자가 플레이어로 변경됩니다. 게임에 대한 보고서가 게임 앱에 대해 자동으로 표시됩니다.
   * **[!UICONTROL 설명]**

      (**Optional**) Type a description for the app.



1. **[!UICONTROL 저장을]** 클릭하여 새 앱을 추가합니다.

   앱이 추가되었으면 앱 정보 페이지에서 추가 옵션 구성에 대해 확인할 수 있습니다. For more information, see [Manage App Settings](/help/using/c-manage-app-settings/c-manage-app-settings.md).