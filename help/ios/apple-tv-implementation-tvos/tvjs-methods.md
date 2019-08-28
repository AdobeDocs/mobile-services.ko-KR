---
description: 다음은 tvOS 라이브러리에서 제공하는 TVJS 메서드 목록입니다.
seo-description: 다음은 tvOS 라이브러리에서 제공하는 TVJS 메서드 목록입니다.
seo-title: TVJS 메서드
solution: Marketing Cloud, Analytics
title: TVJS 메서드
topic: 개발자 및 구현
uuid: A 7 BFA 85 A -0 D 6 E -4 F 51-9 A 9 E -70429 C 2 A 9806
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# TVJS 메서드 {#tvjs-methods}

다음은 tvOS 라이브러리에서 제공하는 TVJS 메서드 목록입니다.

## Configuration methods {#section_5F82FD2F6A0546B3B4E80DF832E11634}

* **버전**

   Adobe Mobile 라이브러리의 현재 버전을 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      version()
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      var sdkVersion = ADBMobile.version();
      ```

   * 반환: `String`

* **privacyStatus**

   현재 사용자에 대한 개인 정보 상태의 NSUInteger 표현을 반환합니다.

   선택 사항은 다음과 같습니다.

   * `ADBMobilePrivacyStatusOptIn`: 히트가 즉시 전송됩니다.
   * `ADBMobilePrivacyStatusOptOut`: 히트는 무시됩니다.
   * `ADBMobilePrivacyStatusUnknown`: 오프라인 추적이 활성화되어 있을 경우, 개인 정보 상태가 옵트인(히트가 전송됨) 또는 옵트아웃(히트가 삭제됨)으로 변경될 때까지 히트를 저장합니다.

      오프라인 추적이 활성화되어 있지 않을 경우, 개인 정보 상태가 옵트인으로 변경될 때까지 히트를 삭제합니다. THe default value is set in the `ADBMobileConfig.json` file.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      privacyStatus()
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      var privacyStatus = ADBMobile.privacyStatus();
      ```

   * 반환: `Number`

* **setPrivacyStatus**

   현재 사용자의 개인 정보 상태를 다음 값 중 하나로 설정합니다.

   * `ADBMobilePrivacyStatusOptIn`: 히트가 즉시 전송됩니다.
   * `ADBMobilePrivacyStatusOptOut`: 히트는 무시됩니다.
   * `ADBMobilePrivacyStatusUnknown`: 오프라인 추적이 활성화되면 개인 정보 상태가 옵트인 (히트를 전송됨) 또는 옵트아웃 (히트가 무시됨) 로 변경될 때까지 히트가 저장됩니다.
   오프라인 추적이 활성화되어 있지 않을 경우, 개인 정보 상태가 옵트인으로 변경될 때까지 히트를 삭제합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      setPrivacyStatus(privacyStatus)
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      ADBMobile.setPrivacyStatus(ADBMobilePrivacyStatusOptIn);
      ```


* **lifetimeValue**

   현재 사용자의 수명 값을 반환합니다. 기본값은 `0`입니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      lifetimeValue()
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      var ltv = ADBMobile.lifetimeValue();
      ```

   * 반환: `Number`

* **userIdentifier**

   사용자 지정 식별자가 설정된 경우 사용자 식별자를 반환합니다. 사용자 지정 식별자가 설정되지 않은 경우 nil을 반환합니다. `nil`기본값은 입니다.

   >[!IMPORTANT]
   >
   >앱 업그레이드가 Experience Cloud 3. x에서 4. x SDK로 업그레이드되면 이전에 사용자 정의 또는 자동 생성된 방문자 ID가 검색하여 사용자 지정 사용자 식별자로 저장됩니다. 이렇게 하면 SDK 업그레이드 시에도 방문자 데이터가 보존됩니다. 4.x SDK에 새로 설치하는 경우 사용자 식별자는 설정할 때까지 nil입니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      userIdentifier()
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      var uid = ADBMobile.userIdentifier();
      ```

   * 반환: `String`

* **setUserIdentifier**

   사용자 식별자를 설정합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      setUserIdentifier(userId)
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      ADBMobile.setUserIdentifier(‘myUserId’);
      ```

   * 반환: 해당 없음

   * 매개 변수:  `userID`

      * 유형: 문자열
      * 이 사용자에 대한 새로운 식별자입니다.

* **setAdvertisingIdentifier**

   SDK에서 IDFA를 설정하고 SDK에 설정된 경우 라이프사이클에서 IDFA가 전송됩니다. 또한 IDFA는 신호(포스트백)에서 액세스할 수 있습니다.

   >[!IMPORTANT]
   >
   >광고 서비스를 사용하는 경우에만 Apple API에서 IDFA를 검색합니다. IDFA를 검색하고 올바르게 사용하지 않으면 앱이 거부될 수 있습니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      setAdvertisingIdentifier(idfa)
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      ADBMobile.setAdvertisingIdentifier(‘myIdfa’);
      ```

   * 반환: 해당 없음
   * 매개 변수: `idfa`
      * 유형: `String`
      * Apple API에서 검색한 IDFA입니다.

* **setDebugLogging**

   디버그 로깅 기본 설정을 설정합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      setDebugLogging(logging)
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      `ADBMobile.setDebugLogging(true);
      ```

   * 반환: 해당 없음
   * 매개 변수: `logging`
      * 유형: `Bool`
      * Adobe SDK가 디버그 콘솔에 로깅해야 하는지 여부를 나타내는 값입니다.


## Analytics methods {#section_F3DB9BE225F84F86BE5F8D15164C0379}

* **trackStateData**

   선택적 컨텍스트 데이터로 앱 상태를 추적합니다. home dashboard, app settings, cart 등과 같이 앱에서 사용할 수 있는 보기를 상태라고 합니다. 이 상태는 웹 사이트의 페이지와 유사하며 trackState 호출은 페이지 보기를 증가시킵니다.

   상태가 비어 있으면 보고서에 앱 이름 앱 버전(빌드)으로 표시됩니다. 보고서에서 이 값이 표시되면 반드시 각 trackState 호출에서 상태를 설정하십시오.

   >[!TIP]
   >
   >페이지 보기를 증가시키는 유일한 추적 호출입니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      trackStateData(stateName [, contextData])
      ```

      * 반환: 해당 없음
      * 매개 변수: `stateName`
         * 유형: `String`
         * 페이지 상태 이름입니다
      * 매개 변수: `contextData`
         * 유형: 객체
         * 이 히트의 추가 컨텍스트 데이터입니다.
   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      ADBMobile.trackStateData(‘homepage’, {‘userid’:12345});
      ```




* **trackActionData**

   앱의 작업을 추적합니다. 작업은 logons, banner taps, feed subscriptions 및 기타 지표 등 앱에서 발생하여 측정하려는 작업입니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      trackActionData(actionName [, contextData])
      ```

      * 반환: 해당 없음
      * 매개 변수: `actionName`
         * 유형: 문자열
         * 추적 중인 작업의 이름입니다.
      * 매개 변수: `contextData`
         * 유형: 객체
         * 이 히트의 추가 컨텍스트 데이터입니다.
   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      ADBMobile.trackActionData(‘likeClicked’, {‘imageName’:’funnyKitty’});
      ```



* **trackLocationWithLatLonData**

   현재 위도 및 경도 좌표를 보냅니다.

   `ADBMobileConfig.json` 또한 파일에 정의된 관심 영역 (POI) 를 사용하여 매개 변수로 입력한 위치가 POIS에 있는지 확인합니다. 정의된 POI 내에 현재 좌표가 있는 경우 컨텍스트 데이터 변수를 채워 `trackLocation` 호출로 전송합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      trackLocationWithLatLonData(lat, lon [, contextData]);
      ```

      * 반환: 해당 없음
      * 매개 변수: `lat`
         * 유형: 숫자
         * 위치의 위도입니다.
      * 매개 변수: `lon`
         * 유형: 숫자
         * 위치의 경도입니다.
      * 매개 변수: `contextData`
         * 유형: 객체
         * 이 히트의 추가 컨텍스트 데이터입니다.
   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      ADBMobile.trackLocationWithLatLonData(43.36, -116.12, null);
      ```




* **trackLifetimeValueIncreaseJsData**

   사용자의 라이프타임 값에 양을 추가합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      trackLifetimeValueIncreaseJsData(increaseAmount)
      ```

      * 반환: 해당 없음
      * 매개 변수: `increaseAmount`
         * 유형: 숫자
         * 사용자의 현재 라이프타임 값에 추가하는 양입니다.
   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      ADBMobile.trackLifetimeValueIncreaseJsData(5);
      ```


* **trackTimedActionStartData**

   이름 작업으로 시간 제한 작업을 시작합니다. 이미 시작한 작업에 대해 이 메서드를 호출하는 경우 이전 시간 제한 작업을 덮어씁니다.

   >[!TIP]
   >
   >이 호출은 히트를 전송하지 않습니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      trackTimedActionStartData(name [, contextData])
      ```

      * 반환: 해당 없음
      * 매개 변수: `name`
         * 유형: 문자열
         * 시작하는 시간 작업의 이름입니다.
      * 매개 변수: `contextData`
         * 유형: 객체
         * 이 히트의 추가 컨텍스트 데이터입니다.
   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      ADBMobile.trackTimedActionStartData(‘level1’, {‘userId’:42423});
      ```


* **trackTimedActionUpdateData**

   데이터를 전달하여 제공된 작업과 관련된 컨텍스트 데이터를 업데이트합니다.

   전달한 데이터는 지정된 작업의 기존 데이터에 추가되며 작업에 대해 동일한 키가 이미 정의된 경우 데이터를 덮어씁니다.

   >[!TIP]
   >
   >이 호출은 히트를 전송하지 않습니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      trackTimedActionUpdateData(name [, contextData])
      ```

      * 반환: 해당 없음
      * 매개 변수: `name`
         * 유형: 문자열
         * 업데이트되는 시간 작업의 이름입니다.
      * 매개 변수: `contextData`
         * 유형: 객체
         * 이 히트의 추가 컨텍스트 데이터입니다.
   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      ADBMobile.trackTimedActionUpdateData(‘level1’);
      ```



* **trackTimedActionEndJsLogic**

   시간 제한 작업을 종료합니다.

   콜백 함수를 제공하면 최종 시간 값에 액세스할 수 있습니다. 콜백이 제공되지 않거나 콜백이 true를 반환하면 Adobe SDK는 자동으로 히트를 전송합니다. 콜백에서 false가 반환되면 시간 제한 작업 히트가 억제됩니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      trackTimedActionEndJsLogic(name [, callback])
      ```

      * 반환: 해당 없음
      * 매개 변수: `name`
         * 유형: 문자열
         * 종료되는 시간 작업의 이름입니다.
      * 매개 변수: `callback`
         * 유형: `function(inAppDuration, totalDuration, data)`
         * Callback method that will have `inAppDuration` (number), `totalDuration` (number), and `data` (context data object) in its parameters.

            You can suppress the final hit from being sent by the SDK by returning `false` in your callback function.
      * 다음은 이 메서드의 코드 샘플입니다.

         ```objective-c
         ADBMobile.trackTimedActionEndJsLogic(‘level1’, 
         function(inAppDuration, totalDuration, data) {
             // do something with final values
             return true;
             });
         ```



* **trackingTimedActionExistsJs**

   시간 작업이 진행 중인지 여부를 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      trackingTimedActionExistsJs(name)
      ```

      * 반환: 부울값
      * 매개 변수: `name`
         * 유형: `String`
         * 존재를 확인해야 하는 Timed Action의 이름입니다.
   * 다음은 이 메서드의 코드 샘플입니다.


      ```objective-c
      var actionExists = ADBMobile.trackTimedActionExistsJs(‘level1’);
      ```


* **trackingIdentifier**

   자동 생성된 방문자 식별자를 반환합니다.

   이 식별자는 Adobe 서버에서 생성된 앱별 고유 방문자 ID입니다. 생성 당시 Adobe 서버에 도달할 수 없는 경우, Apple CFUUID를 사용하여 생성됩니다. 이 값은 처음 실행 시 생성된 다음 저장되며 그 이후부터 사용됩니다. 이 ID는 앱 업그레이드 시에도 보존되고, 표준 애플리케이션 백업 프로세스 중 저장 및 복원되며, 앱을 제거하면 삭제됩니다.

   >[!TIP]
   >
   >앱 업그레이드가 Experience Cloud 3. x에서 4. x SDK로 업그레이드되면 이전에 사용자 정의 또는 자동 생성된 방문자 ID가 검색하여 사용자 지정 사용자 식별자로 저장됩니다. 이렇게 하면 SDK 업그레이드 시에도 방문자 데이터가 보존됩니다. For new installations on the 4.x SDK, the user identifier is `nil`, and the tracking identifier is used. 자세한 내용은 아래의 userIdentifier 행을 참조하십시오.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      trackingIdentifier()
      ```

      * 반환: `String`
      * 매개 변수: 없음
   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      var trackingId = ADBMobile.trackingIdentifier();
      ```


* **trackingSendQueuedHits**

   현재 큐에 올라가 있는 히트 개수와 상관없이 라이브러리에서 오프라인 큐의 모든 히트를 강제로 보냅니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      trackingSendQueuedHits()
      ```

      * 반환: 해당 없음
      * 매개 변수: 없음
   * 다음은 이 메서드의 코드 샘플입니다.


      ```objective-c
      ADBMobile.trackingSendQueuedHits();
      ```


* **trackingClearQueue**

   오프라인 큐에서 모든 히트를 지웁니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      trackingClearQueue()
      ```

      * 반환: 해당 없음
      * 매개 변수: 없음
   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      ADBMobile.trackingClearQueue();
      ```


* **trackingGetQueueSize**

   현재 오프라인 큐에 올라가 있는 히트 수를 검색합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      trackingGetQueueSize()
      ```

      * 반환: 숫자
      * 매개 변수: 없음
   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      var queueSize = ADBMobile.trackingGetQueueSize();
      ```


## Audience Manager methods {#section_0155C4DF04644EDAAF6159C420A158DE}

* **audienceVisitorProfile**

   가장 최근 획득한 방문자 프로필을 반환합니다.

   아직 어떤 신호도 제출되지 않은 경우 null을 반환합니다. 방문자 프로필은 앱이 여러 번 시작되는 경우에도 쉽게 액세스할 수 있도록 `NSUserDefaults`에 저장됩니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      audienceVisitorProfile()
      ```

      * 반환: 객체
      * 매개 변수: 없음
   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      var profile = ADBMobile.audienceVisitorProfile();
      ```


* **audienceDpid**

   현재 DPID를 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      audienceDpid()
      ```

      * 반환: 문자열
      * 매개 변수: 없음
   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      var dpid = ADBMobile.audienceDpid();
      ```


* **audienceDpuuid**

   현재 DPUUID를 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      audienceDpuuid()
      ```

      * 반환: `String`
      * 매개 변수: 없음
   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      var dpuuid = ADBMobile.audienceDpuuid();
      ```


* **audienceSetDpidDpuuid**

   dpid 및 dpuuid를 설정하고 설정되어 있으면 각 신호와 함께 전송합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      audienceSetDpidDpuuid(dpid, dpuuid)
      ```

      * 반환: 해당 없음
      * 매개 변수: `dpid`
         * 유형: `String`
         * Audience Manager의 데이터 제공자 ID입니다.
      * 매개 변수: `dpuuid`
         * 유형: `String`
         * 사용자 및 데이터 제공자 조합의 식별자입니다.
   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      ADBMobile.audienceSetDpidDpuuid(‘myDpid’, ‘userDpuuid’);
      ```


* **audienceSignalWithDataJsCallback**

   Audience Manager에 트레이트를 포함한 신호를 전송하고 콜백 함수에서 반환하는 일치 세그먼트를 가져옵니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      audienceSignalWithDataJsCallback(traits [, callback])
      ```

      * 매개 변수: `traits`
         * 유형: 객체
         * 이 사용자의 트레이트 사전입니다.
      * 매개 변수: `callback`
         * 유형: 함수(profile)
         * Audience Manager를 통해 콜백 함수용 매개 변수에서 반환된 프로필입니다.
   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      ADBMobile.audienceSignalWithDataJsCallback({‘trait’:’something’}, 
      function(profile) {
          //do something with the user’s segments found in profile
           });
      ```



* **audienceReset**

   Audience Manager UUID를 재설정하고 현재 방문자 프로필을 삭제합니다.

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      audienceReset()
      ```

      * 반환: 해당 없음
      * 매개 변수: 없음
   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      ADBMobile.audienceReset();
      ```


## ID Service methods {#section_BEB6DA612EA4423FB354B65ECC941335}

* **visitorMarketingCloudID**

   ID 서비스에서 Experience Cloud ID를 검색합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      visitorMarketingCloudID()
      ```

      * 반환: 문자열
      * 매개 변수: 없음
   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      var mcid = ADBMobile.visitorMarketingCloudID();
      ```


* **visitorSyncIdentifiers**

   Experience Cloud ID 외에도 각 방문자에 연결할 추가 고객 ID를 설정할 수 있습니다. 방문자 API는 여러 다른 고객 ID의 범위를 구분하기 위해 동일한 방문자의 여러 고객 ID와 고객 유형 식별자를 수락합니다. 이 메서드는 JavaScript 라이브러리의 setCustomerID에 해당합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      visitorSyncIdentifiers(identifiers)
      ```

      * 반환: 해당 없음
      * 매개 변수: `identifiers`

         * 유형: `Object`
         * 이 사용자의 ID 서비스에 동기화할 식별자입니다.
   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      ADBMobile.visitorSyncIdentifiers({‘idType’:’idValue’});
      ```


* **visitorSyncIdentifiersAuthenticationState**

   제공된 식별자를 ID 서비스에 동기화합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      visitorSyncIdentifiersAuthenticationState(identifiers, authState)
      ```

      * 반환: 해당 없음
      * 매개 변수: `identifiers`
         * 유형: `Object`
         * 이 사용자의 ID 서비스에 동기화할 식별자입니다.
      * 매개 변수: `authState`
         * 유형: ADBMobileVisitorAuthenticationState
         * 사용자의 인증 상태 및 가능한 값은 다음과 같습니다.
            * `ADBMobileVisitorAuthenticationStateUnknown`
            * `ADBMobileVisitorAuthenticationStateAuthenticated`
            * `ADBMobileVisitorAuthenticationStateLoggedOut`
   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      ADBMobile.visitorSyncIdentifiersAuthenticationState({'myIdType':'valueForUser'}, ADBMobileVisitorAuthenticationStateLoggedOut)
      ```



* **visitorSyncIdentifierWithTypeIdentifierAuthenticationState**

   제공된 식별자 유형 및 값을 ID 서비스에 동기화합니다. 

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      visitorSyncIdentifierWithTypeIdentifierAuthenticationState(idType, identifier, authState)
      ```

      * 반환: N/A
      * 매개 변수: `idType`
         * 유형: `String`
         * 동기화 중인 식별자의 유형입니다.
      * 매개 변수: `identifier`
         * 유형: `String`
         * 동기화 중인 식별자의 값입니다.
      * 매개 변수: `authState`
         * 유형: Adbmobilevisitorauthenticationstate
인증 상태. 가능한 값은 다음과 같습니다.
            * `ADBMobileVisitorAuthenticationStateUnknown`
            * `ADBMobileVisitorAuthenticationStateAuthenticated`
            * `ADBMobileVisitorAuthenticationStateLoggedOut`
   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      ADBMobile.visitorSyncIdentifierWithTypeIdentifierAuthenticationState('myIdType', 'valueForUser', 
      ADBMobileVisitorAuthenticationStateAuthenticated);
      ```


* **visitorGetIDsJs**

   읽기 전용 ADBVisitorID 개체 배열을 검색합니다. 다음 코드 샘플은 VisitorID 개체의 예제입니다.

   ```js
   {
       idType: "abc",
       authenticationState: 1, 
       identifier: "123"
   }
   ```

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      visitorGetIDsJs()
      ```

      * 반환: `Array [Object]`

      * 매개 변수: 없음
   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      var myVisitorIds = ADBMobile.visitorGetIDsJs();
      ```


## Target methods {#section_F9F7EC2B9B7C41AFBCA2458F9F138634}

* **targetThirdPartyID**

   타사 ID를 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      targetThirdPartyID()
      ```

      * 반환: `String`
      * 매개 변수: 없음
   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      var thirdPartyID = ADBMobile.targetThirdPartyID();
      ```


* **targetSetThirdPartyID**

   타사 ID를 설정합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      targetSetThirdPartyID(thirdPartyID)
      ```

      * 반환: 해당 없음
      * 매개 변수: `thirdPartyID`
         * 유형: `String`
         * 대상 요청에 사용할 타사 ID입니다.
   * 다음은 이 메서드의 코드 샘플입니다.
   ```objective-c
   ADBMobile.targetSetThirdPartyID(‘thirdPartyID’);
   ```

* **targetPcID**

   PcID를 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      targetPcID()
      ```

      * 반환: `String`
      * 매개 변수: 없음
   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      var pcID = ADBMobile.targetPcID();
      ```


* **targetSessionID**

   세션 ID를 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      targetSessionID()
      ```

      * 반환: `String`
      * 매개 변수: 없음
   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      var sessionID = ADBMobile.targetSessionID();
      ```