---
description: Windows 8.1 Universal App Store 라이브러리에서 제공하는 클래스 및 메서드입니다.
seo-description: Windows 8.1 Universal App Store 라이브러리에서 제공하는 클래스 및 메서드입니다.
seo-title: SDK 메서드
solution: Marketing Cloud, Analytics
title: SDK 메서드
topic: 개발자 및 구현
uuid: 0 F 558 FF 4-73 D 3-4439-9 D 51-62 FBD 74 D 2 CEA
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# SDK methods {#sdk-methods}

Windows 8.1 Universal App Store 라이브러리에서 제공하는 클래스 및 메서드입니다.

>[!TIP]
>
>When you consume `winmd` methods from winJS (JavaScript), all methods automatically have their first letter lowercased.

* **Getversion (winjs: Getversion)**

   Adobe Mobile 라이브러리의 현재 버전을 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      static Platform::String ^GetVersion();
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
      varADB = ADBMobile;var libVersion = ADB.Config.getVersion(); 
      ```

* **Getprivacystatusasync (winjs: Getprivacystatusasync)**

   현재 사용자에 대한 개인 정보 상태의 열거 표현을 반환합니다.

   * `ADBMobilePrivacyStatusOptIn` - 히트가 즉시 전송됩니다.
   * `ADBMobilePrivacyStatusOptOut` - 히트는 무시됩니다.
   * `ADBMobilePrivacyStatusUnknown` - 보고서 세트에 타임스탬프가 사용되면 개인정보 상태가 옵트인(히트가 전송됨) 또는 옵트아웃(히트가 삭제됨)으로 변경될 때까지 히트가 저장됩니다. 보고서 세트에 타임스탬프가 사용되지 않으면 개인정보 상태가 옵트인으로 변경될 때까지 히트가 삭제됩니다.

      The default value is set in the [ADBMobileConfig.json config](/help/windows-appstore/c-configuration/c.json.md) file.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      static Windows::Foundation::IAsyncOperation<ADBMobilePrivacyStatus> ^getPrivacyStatusAsync(); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```csharp
      public enum class ADBMobilePrivacyStatus : int  {
        ADBMobilePrivacyStatusOptIn = 1, 
        ADBMobilePrivacyStatusOptOut =  2,
        ADBMobilePrivacyStatusUnknown = 3
      };
      ```

      ```js
      var ADB = ADBMobile;
      var status;
      ADB.Config.getPrivacyStatusAsync.then(function(privacyStatus) {
      status = privacyStatus;
      }); 
      ```

* **Setprivacystatus (winjs: Setprivacystatus)**

   현재 사용자의 개인정보 상태를 `status`로 설정합니다. 다음 값 중 하나를 설정합니다.

   * `ADBMobilePrivacyStatusOptIn` - 히트가 즉시 전송됩니다.
   * `ADBMobilePrivacyStatusOptOut` - 히트는 무시됩니다.
   * `ADBMobilePrivacyStatusUnknown` - 보고서 세트에 타임스탬프가 사용되면 개인정보 상태가 옵트인(히트가 전송됨) 또는 옵트아웃(히트가 삭제됨)으로 변경될 때까지 히트가 저장됩니다. 보고서 세트에 타임스탬프가 사용되지 않으면 개인정보 상태가 옵트인으로 변경될 때까지 히트가 삭제됩니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      static void SetPrivacyStatus(ADBMobilePrivacyStatus status);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```csharp
      public enum class ADBMobilePrivacyStatus : int {
        ADBMobilePrivacyStatusOptIn = 1,
        ADBMobilePrivacyStatusOptOut = 2,
        ADBMobilePrivacyStatusUnknown = 3
        }; 
      ```

      ```js
      var ADB = ADBMobile;
      ADB.Config.setPrivacyStatus(ADB.ADBMobilePrivacyStatus.adbmobilePrivacyStatusOptIn); 
      ```

* **Getlifetimevalue (winjs: Getlifetimevalue)**

   현재 사용자의 수명 값을 반환합니다. 기본값은 0입니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      static float GetLifetimeValue();
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
       var ADB = ADBMobile;
       var ltv = ADB.Config.getLifetimeValue(); 
      ```

* **Getuseridentifier (winjs: Getuseridentifier)**

   사용자 지정 식별자가 설정된 경우 사용자 지정 사용자 식별자를 반환합니다. 사용자 지정 식별자가 설정되지 않은 경우 null을 반환합니다. 기본값은 `null`입니다.

   >[!TIP]
   >
   >앱 업그레이드가 Experience Cloud 3. x에서 4. x SDK로 업그레이드되는 경우 이전 ID (사용자 정의 또는 자동 생성) 가 검색하여 사용자 지정 사용자 식별자로 저장됩니다. 이렇게 하면 SDK 업그레이드 시에도 방문자 데이터가 보존됩니다. 4.x SDK에 새로 설치하는 경우 사용자 식별자는 설정될 때까지 `null`입니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      static Platform::String^GetUserIdentifier();
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
      var ADB = ADBMobile;
      var userId = ADB.Config.getUserIdentifier(); 
      ```

* **Setuseridentifier (winjs: Setuseridentifier)**

   사용자 식별자를 `identifier`로 설정합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      static void SetUserIdentifier(Platform::String ^userIdentifier);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
      var ADB = ADBMobile;
      ADB.Config.setUserIdentifier("someUserId"); 
      ```

* **Getdebuglogging (winjs: Getdebuglogging)**

   현재 디버그 로깅 기본 설정을 반환합니다. 기본값은 `false`입니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      static bool GetDebugLogging(); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
      var ADB = ADBMobile;
      var logging = ADB.Config.getDebugLogging(); 
      ```

* **Setdebuglogging (winjs: Setdebuglogging)**

   디버그 로깅 기본 설정을 `debugLogging`으로 설정합니다. 디버그 로깅은 라이브러리의 디버그 버전을 사용하는 경우에만 작동합니다. 릴리스 버전은 이 설정을 무시합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      static void SetDebugLogging(bool debugLogging); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
      var ADB = ADBMobile;
      ADB.Config.setDebugLogging(true); 
      ```

* **Collectlifecycledata (winjs: Collectlifecycledata)**

   SDK의 솔루션 전체에서 사용하기 위해 라이프사이클 데이터를 수집해야 함을 SDK에 표시합니다. 자세한 내용은 [라이프사이클 지표](/help/windows-appstore/metrics.md)를 참조하십시오.

   >[!TIP]
   >
   >Invoke this method in the `onResume()` method in each Activity inside of your application, as shown in the following example. 또한 글로벌 애플리케이션 컨텍스트 대신 컨텍스트 개체로 활동 또는 서비스를 전달하는 것이 좋습니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      static void CollectLifecycleData();
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
      var ADB = ADBMobile;
      ADB.Config.collectLifecycleData(); 
      ```

* **Pausecollectinglifecycledata (winjs: Pausecollectinglifecycledata)**

   라이프사이클 지표를 정확히 계산하기 위해 앱이 일시 중지되었음을 SDK에 표시합니다. 예를 들어, OnPause에서 타임스탬프를 수집하여 기존 세션 길이를 파악합니다. 플래그를 설정하여 앱이 충돌하지 않았음을 라이프사이클에서 정확히 알도록 할 수도 있습니다. 자세한 내용은 [라이프사이클 지표](/help/windows-appstore/metrics.md)를 참조하십시오.

   >[!TIP]
   >
   >Invoke this method in the `onPause()` methods in each Activity inside Your application, as shown in the example. 또한 글로벌 애플리케이션 컨텍스트 대신 컨텍스트 개체로 활동 또는 서비스를 전달하는 것이 좋습니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      static void PauseCollectingLifecycleData();
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
      var ADB = ADBMobile;
      ADB.Config.pauseCollectingLifecycleData();
      ```