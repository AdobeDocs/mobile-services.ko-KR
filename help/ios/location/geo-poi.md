---
description: 지리적 위치는 iOS 앱에서 위도와 경도 및 사전 정의된 관심 영역을 사용하여 위치 데이터를 측정할 수 있도록 합니다.
seo-description: 지리적 위치는 iOS 앱에서 위도와 경도 및 사전 정의된 관심 영역을 사용하여 위치 데이터를 측정할 수 있도록 합니다.
seo-title: 지리적 위치 및 관심 영역
solution: Marketing Cloud, Analytics
title: 지리적 위치 및 관심 영역
topic: 개발자 및 구현
uuid: c 800 ec 85-a 33 f -425 d-b 28 f-bfe 8 bf 229 ae 8
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Geo-location and points of interest {#geo-location-and-points-of-interest}

지리적 위치는 iOS 앱에서 위도와 경도 및 사전 정의된 관심 영역을 사용하여 위치 데이터를 측정할 수 있도록 합니다.

각 `trackLocation` 호출에서는 다음 정보를 보냅니다.

* Adobe Mobile Services에 정의된 관심 영역(POI)의 위도, 경도 및 위치.

   이 정보는 자동 보고를 위해 모바일 솔루션 변수로 전달됩니다.

* 중심으로부터 떨어진 거리 및 정확도 - 컨텍스트 데이터로 전달됨.

   이러한 변수는 자동으로 캡처되지 않습니다. You must map these context data variables by using the instructions in *Sending Additional Data* section below.

## 동적 POI 업데이트 {#section_3747B310DD5147E2AAE915E762997712}

버전 4.2부터 POI는 Adobe Mobile 인터페이스에서 정의되며 앱 구성 파일과 동적으로 동기화됩니다. This synchronization requires an `analytics.poi` setting in the `ADBMobile.json` file:

```js
“analytics.poi”: “https://assets.adobedtm.com/…/yourfile.json”,
```

자세한 내용은 [Adbmobile JSON 구성을](/help/ios/configuration/json-config/json-config.md)참조하십시오.

구성되지 않은 경우 `ADBMobile.json` 파일의 업데이트된 버전을 다운로드하여 앱에 추가해야 합니다. 자세한 내용 및 지침은 시작하기 *전에* SDK [및 테스트 도구 다운로드를](/help/ios/getting-started/requirements.md)참조하십시오.

## 지리적 위치 및 POI 추적 {#section_B1616E400A7548F9A672F97FEC75AE27}

1. 프로젝트에 라이브러리를 추가하고 라이프사이클을 구현합니다.

   자세한 내용은 핵심 구현 *및* 라이프사이클에서 [프로젝트에 SDK 및 구성 파일 추가를](/help/ios/getting-started/dev-qs.md)참조하십시오.
1. 라이브러리를 가져옵니다:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. `trackLocation`을 호출하여 현재 위치를 추적합니다.

   ```objective-c
   CLLocation *currentLocation = location; 
   [ADBMobile trackLocation: currentLocation data: nil]; 
   ```

   >[!TIP]
   >
   >`trackLocation` 언제든지 전화할 수 있습니다.

   호출에 전달되는 위치를 결정하려면 사용자 `trackLocation` 위치 [가져오기를 사용합니다](https://developer.apple.com/Library/ios/documentation/UserExperience/Conceptual/LocationAwarenessPG/CoreLocation/CoreLocation.html).

또한 정의된 POI 반경 내에 위치가 있는 것으로 확인되면 `a.loc.poi` 컨텍스트 데이터 변수가 `trackLocation` 히트와 함께 전송되며 위치 보고서에서 POI로 보고됩니다. `a.loc.dist` 컨텍스트 변수도 정의된 좌표로부터 떨어진 거리(단위: 미터)와 함께 전송됩니다.

## Send additional data {#section_3EBE813E54A24F6FB669B2478B5661F9}

위치 데이터 외에, 각 위치 추적 호출로 추가 컨텍스트 데이터를 전송할 수 있습니다.

```objective-c
NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
[contextData setObject:@"GPS" forKey:@"myapp.location.LocationSource"]; 
[ADBMobile trackLocation: currentLocation data:contextData];
```

컨텍스트 데이터 값은 사용자 지정 변수에 매핑되어야 합니다.

![](assets/map-location-context-data.png)

## Location context data {#section_FFB71E6653F9410A89CC6ACC0C9164A9}

위도와 경도는 총 6개의 컨텍스트 데이터 매개 변수에 대해 각각 서로 다른 정밀도 수준을 나타내는 세 가지 컨텍스트 데이터 매개 변수를 사용하여 전송됩니다.

예를 들어 위도 40.93231 및 경도 -111.93152인 좌표는 정밀도가 1m인 위치를 나타냅니다. 이 위치는 정밀도 수준에 따라 다음 변수에 대해 분할됩니다.

* `a.loc.lat.a`= 040.9
* `a.loc.lat.b` = 32
* `a.loc.lat.c` = 31
* `a.loc.lon.a` = -111.9
* `a.loc.lon.b` = 31
* `a.loc.lon.c` = 52

일부 정밀도 수준은 현재 위치의 정확도에 따라 "00"으로 나타날 수도 있습니다. 예를 들어 위치가 현재 100m까지 정확하면 `a.loc.lat.c` 및 `a.loc.lon.c`에 "00" 값이 채워집니다.

## 추가 정보 {#section_931AC1E0D88147E29FE1B6E3CC1E9550}

다음 정보를 숙지하십시오.

* `trackLocation` 요청은 호출과 동일한 방식으로 전송됩니다 `trackAction` .

* POI는 일반적인 `trackAction` 및 `trackState` 호출의 일부로 전달되지 않으므로, POI를 추적하려면 `trackLocation` 호출을 사용해야 합니다.

* `trackLocation`은 위치 및 POI를 추적하는 데 필요한 만큼 자주 호출해야 합니다.

   앱이 시작될 때 `trackLocation`을 호출한 다음 필요할 경우 앱의 요구 사항을 기반으로 호출하는 것이 좋습니다.

* POI는 앱 구성 파일에서 정의된 후에만 그 값이 채워집니다.

   POI는 이전에 전송된 과거 `trackLocation` 호출에는 적용되지 않습니다.
* `trackLocation` 호출은 `trackAction` 호출과 유사하게, 추가 컨텍스트 데이터 전송을 지원합니다.

* 두 POI의 지름이 겹치는 경우 현재의 위치가 포함된 첫 번째 POI가 사용됩니다.

   POI가 겹치는 경우 가장 세분화된 POI가 보고되도록 세분화 정도가 가장 높은 항목에서 가장 낮은 항목의 순서로 POI를 나열해야 합니다.
