---
description: 이 섹션에서는 이전 Windows mobile SDK의 3.x 버전에서 Experience Cloud 솔루션용 Universal Windows Platform 4.x SDK로 마이그레이션하는 방법에 대해 설명합니다.
seo-description: 이 섹션에서는 이전 Windows mobile SDK의 3.x 버전에서 Experience Cloud 솔루션용 Universal Windows Platform 4.x SDK로 마이그레이션하는 방법에 대해 설명합니다.
seo-title: 4. x로 마이그레이션
solution: Marketing Cloud, Analytics
title: 4. x로 마이그레이션
topic: 개발자 및 구현
uuid: BDD 6 C 5 CD -3892-4 E 99-B 69 E -77105 AD 66 E 25
translation-type: tm+mt
source-git-commit: 68bc21f1c6dba2faeed332495592114af90c8f61

---


# 4. x SDK로 마이그레이션{#migrate-to-x}

이 섹션에서는 3. x 버전의 Windows Mobile SDK에서 Experience Cloud 솔루션용 Universal Windows Platform 4. x SDK로 마이그레이션하는 방법에 대해 설명합니다.

이제 버전 4. x로 이동하면 정적 메서드를 통해 모든 기능에 액세스할 수 있습니다. 더 이상 자신의 개체를 추적할 필요가 없습니다.

다음 섹션에서는 버전 3.x에서 버전 4.x로 마이그레이션하는 방법을 설명합니다.

## Remove unused properties {#section_145222EAA20F4CC2977DD883FDDBBFC5}

다운로드에 새 `ADBMobileConfig.json` 파일이 포함됩니다. 이 파일은 애플리케이션별 전역 설정을 포함하며, 이전 버전에서 사용된 대부분의 구성 변수를 대체합니다.

다음은 `ADBMobileConfig.json` 파일 예제입니다.

```js
{ 
    "version" : "1.0", 
    "analytics" : { 
        "rsids" : "coolApp", 
        "server" : "my.CoolApp.com", 
        "charset" : "UTF-8", 
        "ssl" : true, 
        "offlineEnabled" : true, 
        "lifecycleTimeout" : 300, 
        "privacyDefault" : "optedin", 
        "poi" : [ 
                    ["san francisco",37.757144,-122.44812,7000], 
                    ["santa cruz",36.972935,-122.01725,600] 
                ] 
    }, 
 "target" : { 
  "clientCode" : "myTargetClientCode", 
  "timeout" : 5 
 }, 
 "audienceManager" : { 
  "server" : "myServer.demdex.com" 
 } 
}
```

다음 표에는 구성 파일로 이동하는 데 필요한 구성 변수가 나열되어 있습니다. 첫 번째 열의 변수에 대해 설정된 값을 두 번째 열의 변수로 이동한 뒤 코드에서 이전 구성 변수를 제거합니다.

### 3.x에서 마이그레이션 중

다음 표에서는 3. x SDK의 변수 목록과 4. x SDK의 새 이름을 제공합니다.

| 구성 변수/메서드 | Variable in the `ADBMobileConfig.json` file. |
|--- |--- |
| offlineTrackingEnabled | "offlineEnabled" |
| reportSuiteIDs | "rsids" |
| trackingServer | "server" |
| charSet | "charset" |
| currencyCode | "currency" |
| ssl | "ssl" |
| setOfflineHitLimit | 제거합니다. 더 이상 사용되지 않습니다. |
| linkTrackVars | 제거합니다. 더 이상 사용되지 않습니다. |
| linkTrackEvents | 제거합니다. 더 이상 사용되지 않습니다. |

## Update track calls and tracking variables {#section_96E7D9B3CDAC444789503B7E7F139AB9}

버전 4 SDK는 웹 중심의 `Track` 및 `TrackLink` 호출 대신 모바일에서 좀더 이해하기 쉬운 두 가지 방법을 사용합니다.

* `TrackState`상태는 'home dashboard', 'app settings', 'cart' 등과 같이 앱에서 사용할 수 있는 보기입니다. 이 상태는 웹 사이트의 페이지와 유사하며 `trackState` 호출은 페이지 보기를 증가시킵니다.

* `TrackAction` 작업은 'logons,' 'banner taps,' 'feed subscriptions' 및 기타 지표 등 앱에서 발생하여 측정하려는 작업입니다. 이러한 호출은 페이지 보기 횟수를 증가시키지 않습니다.

이 두 메서드의 `contextData` 매개 변수는 컨텍스트 데이터로 전송되는 이름 - 값 쌍을 포함합니다.

### 이벤트, prop, evar

[SDK 방법을](/help/universal-windows/c-configuration/methods.md)확인한 경우, 이벤트, evar, prop, heirs 및 목록을 설정하는 위치를 생각해 보십시오. 버전 4에서는 더 이상 이러한 유형의 변수를 앱에서 직접 할당할 수 없습니다. 대신 SDK는 컨텍스트 데이터 및 처리 규칙을 사용하여 Analytics 변수에 앱 데이터를 매핑하여 보고합니다.

처리 규칙은 다음과 같은 이점을 제공합니다.

* 앱 스토어에 업데이트를 제출하지 않고도 데이터 매핑을 변경할 수 있습니다.
* 보고서 세트와 관련된 변수를 설정하는 대신 의미 있는 이름을 데이터에 사용할 수 있습니다.
* 추가 데이터를 보내는 작업에는 거의 영향을 미치지 않습니다. 이러한 값은 처리 규칙을 사용하여 매핑될 때까지 보고서에 표시되지 않습니다.

자세한 내용은 분석 개요의 *처리 규칙* 섹션을 [참조하십시오](/help/universal-windows/analytics/analytics.md).

변수에 직접 할당한 값은 대신 컨텍스트 데이터에 추가해야 합니다. This means that calls to `SetProp`, `SetEvar`, and assignments to persistent context data should all be removed and the values added to context data.

### Appsection/서버, geozip, 거래 ID, 캠페인 및 기타 표준 변수

위에 나열된 변수를 포함하여 측정 개체에 설정한 다른 모든 데이터는 대신 컨텍스트 데이터에 추가해야 합니다. 즉, `TrackState` OR `TrackAction` 호출로 전송된 데이터만 `data` 매개 변수의 페이로드입니다.

**추적 호출 바꾸기**

코드에서 다음 메서드를 `trackState` 또는 `trackAction` 호출로 바꿉니다.

**3.x에서 마이그레이션 중:**

* TrackAppState(TrackState)
* TrackEvents(TrackAction)
* Track(TrackAction)
* TrackLinkURL(TrackAction)

## 사용자 지정 ID 서비스 {#section_2CF930C13BA64F04959846E578B608F3}

`visitorID` 변수를 호출로 바꿉니다 `setUserIdentifier`.

## Offline tracking {#section_5D4CD8CD1BE041A79A8657E31C0D24C6}

파일에서 오프라인 추적이 활성화되어 `ADBMobileConfig.json` 있습니다. 다른 모든 오프라인 구성은 자동으로 수행됩니다.

코드에서 다음 메서드 호출을 제거하십시오.

**3.x에서 마이그레이션 중:**

* SetOnline
* SetOffline

## Products variable {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

 변수는 처리 규칙에서 사용할 수 없으므로 다음 구문을 사용하여 `products`products를 설정할 수 있습니다.

```js
// create a processing rule to set the corresponding product event. 
// for example, set the Product Views event when context data a.action = "product view" 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
cdata["&&products"] = ";Cool Shoe"; 
ADB.Analytics.trackAction("product view", cdata);
```

![](assets/prod-view.png)

The value of `"&&products"` (in this example, the value is `";Cool Shoe`") should follow the products string syntax for the type of event that you are tracking.