---
description: 이 확장 기능은 프로젝트에서 Experience Cloud 솔루션 4.x Windows SDK의 참조를 더욱 쉽게 추가할 수 있는 방법을 제공합니다.
seo-description: 이 확장 기능은 프로젝트에서 Experience Cloud 솔루션 4.x Windows SDK의 참조를 더욱 쉽게 추가할 수 있는 방법을 제공합니다.
seo-title: Experience Cloud Solutions 4. x SDK 용 Windows Visual Studio 익스텐션
solution: Marketing Cloud, Analytics
title: Experience Cloud Solutions 4. x SDK 용 Windows Visual Studio 익스텐션
topic: 개발자 및 구현
uuid: E 48 FAF 54-8 B 08-4224-9 D 80-E 553 A 983129 E
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Windows Visual Studio extensions for Experience Cloud Solutions 4.x SDK {#windows-visual-studio-extensions-for-experience-cloud-solutions-x-sdk}

이 익스텐션을 사용하면 Experience Cloud Solutions 4. x Windows SDK의 참조를 프로젝트에 보다 쉽게 추가할 수 있습니다.

## Github에서 라이브러리 설치 {#section_F55DB6241EF1475286C05FEAEBF996A3}

1. [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases)에서 Windows Universal SDK를 다운로드합니다.
1. 다운로드한 파일을 로컬로 압축 해제합니다.
1. **[!UICONTRTOL Adbmobileuniversalwindowsvsix. vsix]** 파일을 두 번 클릭하여 설치 프로그램을 엽니다.
1. **[!UICONTROL [전역 위치]** ] 를 선택하고 라이브러리를 설치합니다.

## Add references to your project {#section_00C14FE9243D4330BE1F4BB56FCF08B1}

1. Windows 10 프로젝트를 엽니다.
1. 참조 관리자 대화 상자를 엽니다.

   ![](assets/ref_manager.png)

1. **[!UICONTROL 확장]** 탭에서 Uicontrol Adobe Mobile SDK **[를 찾아 선택합니다]**.
1. **[!UICONTROL 확인]을 클릭하여 저장합니다.**

   Adobe Mobile SDK가 프로젝트에 추가됩니다. **[Uicontrol Microsoft Visual C + + 런타임]** 패키지가 아직 추가되지 않은 경우 이 패키지는 프로젝트에 추가됩니다.

1. 구성 관리자에서 플랫폼 유형을 선택하고 앱 테스트를 시작합니다.
