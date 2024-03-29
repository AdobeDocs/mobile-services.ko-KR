---
description: 마케팅 링크 추적 및 보고 기능을 사용하려면 SDK 구성에서 획득 추적을 활성화해야 합니다.
keywords: mobile
solution: Experience Cloud Services,Analytics
title: 획득 구성
topic-fix: Metrics
uuid: e996e43e-8a77-47a3-a6fb-53f676f92bef
exl-id: 3a12dfab-70d0-41e6-8d4e-5aba21bb8606
source-git-commit: 7cfaa5f6d1318151e87698a45eb6006f7850aad4
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 100%

---

# 획득 구성 {#configure-acquisition}

{#eol}

마케팅 링크 추적 및 보고 기능을 사용하려면 SDK 구성에서 획득 추적을 활성화해야 합니다.

1. 앱에 대한 앱 설정 관리 페이지에서 **[!UICONTROL SDK 획득 옵션]** 섹션으로 스크롤합니다.
1. 다음 작업을 완료하십시오.

   * 획득을 사용하려면 **[!UICONTROL 활성화]** 확인란을 선택합니다.

      이 확인란을 선택하면 **[!UICONTROL 레퍼러 시간 초과]** 필드가 활성화되고 값이 0에서 5로 변경됩니다.

   * **[!UICONTROL 레퍼러 시간 초과(초)]** 필드에 값을 입력합니다.

      (**선택사항**) **[!UICONTROL 활성화]** 확인란을 활성화하면 이 필드는 선택 사항입니다. 초로 지정된 시간 초과 값을 변경할 수 있습니다. 이 설정은 첫 번째 실행 히트를 보내기 전에 획득 정보를 기다리는 시간을 지정합니다.
   >[!IMPORTANT]
   >0이 아닌 값을 입력해야 합니다. 획득을 활성화하지만 값을 0으로 두면 획득 링크가 작동하지 않습니다. 기본값 5초를 사용하는 것이 좋습니다.

1. 새로운 SDK 구성 파일을 다운로드하여 앱에서 사용합니다.

   **iOS**&#x200B;에 대한 획득을 성공적으로 구성했습니다.
