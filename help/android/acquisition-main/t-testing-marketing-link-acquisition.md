---
description: 다음 지침은 Android 장치에서 마케팅 링크로 획득 캠페인을 라운드트립 하는 데 도움이 됩니다.
keywords: Android; 라이브러리; 모바일; SDK
seo-description: 다음 지침은 Android 장치에서 마케팅 링크로 획득 캠페인을 라운드트립 하는 데 도움이 됩니다.
seo-title: 마케팅 링크 획득 테스트
solution: Marketing Cloud, Analytics
title: 마케팅 링크 획득 테스트
topic: 개발자 및 구현
uuid: D 0933 DCC -8 FC 3-4 F 60-987 F -7 A 54559 AACF 5
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Testing Marketing Link acquisition {#testing-marketing-link-acquisition}

다음 지침은 Android 장치에서 마케팅 링크로 획득 캠페인을 라운드트립 하는 데 도움이 됩니다.

모바일 앱이 Google Play에 아직 없는 경우 마케팅 링크를 만들 때 모바일 앱을 대상으로 선택할 수 있습니다. 이 작업은 획득 링크를 클릭한 후 획득 서버가 사용자를 리디렉션하는 앱에만 영향을 주며, 획득 링크를 테스트하는 기능에는 영향을 주지 않습니다. 쿼리 문자열 매개 변수는 Google Play 스토어에 전달되며, 설치할 때 캠페인 브로드캐스트의 일부로 앱에 전달됩니다. 왕복 모바일 앱 획득 테스트에는 이러한 유형의 브로드캐스트 시뮬레이션이 필요합니다.

The app must be freshly installed, or have data cleared in **[!UICONTROL Settings]**, each time a test is run. 이렇게 하면 앱을 처음 시작할 때 캠페인 쿼리 문자열 매개 변수와 연결된 초기 라이프사이클 지표를 전달할 수 있습니다.

1. [모바일 앱 확보에서](/help/android/acquisition-main/acquisition.md) 사전 요구 사항을 완료하고, 브로드캐스트 수신기를 올바르게 `INSTALL_REFERRER`구현했는지 확인합니다.
1. In the Adobe Mobile Services] UI, click  **[!UICONTROL Acquisition]** &gt; **[!UICONTROL Marketing Links Builder]** and generate an Acquisition Marketing Link URL that sets Google Play as the destination for Android devices.

   자세한 정보는 [마케팅 링크 빌더](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md)를 참조하십시오.

   예:

   `https://c00.adobe.com/v3/da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d/start?a_dl=573e5bb3248a501360c2890b`

1. 생성된 링크를 Android 장치에서 엽니다.

   다음 예와 비슷한 URL이 포함된 페이지로 리디렉션해야 합니다.

   `https://play.google.com/store/apps/details?id=com.adobe.android&referrer=utm_campaign%3Dadb_acq_v3%26utm_source%3Dadb_acq_v3%26utm_content%3D91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`

1. Copy the unique ID after `utm_content%3D`.

   이전 예에서 ID는 `91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`입니다.

   장치에서 고유 ID를 가져올 수 없을 경우 바탕 화면에서 다음 `CURL` 명령을 실행하여 응답 문자열에서 고유 ID를 가져옵니다.

   `curl -A "Mozilla/5.0 (Linux; Android 5.0.2; SAMSUNG SM-T815Y Build/LRX22G) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/44.0.2403.133 Safari/537.36" <Your Marketing Link>`

   예:

   `curl -A "Mozilla/5.0 (Linux; Android 5.0.2; SAMSUNG SM-T815Y Build/LRX22G) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/44.0.2403.133 Safari/537.36" https://c00.adobe.com/v3/da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d/start?a_dl=573e5bb3248a501360c2890b`

1. 3단계의 고유 ID를 사용하여 다음 형식의 획득 종료 링크를 구성합니다.

   `https://c00.adobe.com/v3/<appid>/end?a_ugid=<unique id>`

   예, `https://c00.adobe.com/v3/<appid>/end?a_ugid=91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`

1. 브라우저에서 링크를 엽니다.

   JSON 응답에 `contextData`가 표시되어야 합니다.

   ```
   {"fingerprint":"44b2f88a062df7e727c047f006deb9971304617b","endCallbacks":["***"],"timestamp":1464301282,"appguid":"da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d","contextData": 
   {"a.launch.campaign.trackingcode":"trymttvm","a.referrer.campaign.name":"Android Demo","a.referrer.campaign.trackingcode":"trymttvm"} 
   ,"adobeData":{"unique_id":"9a2be52764a8db125c29a8c10f3b1b3d5d8ed915","deeplinkid":"57476c26072932ec6d3a470b"}}.
   ```

1. 3단계를 반복하여 새 고유 ID를 얻습니다.
1. 구성 파일에서 다음 설정이 올바른지 확인합니다.

   | 이 예에서 | 값 |
   |--- |--- |
   | acquisition | 서버가 있어야 `c00.adobe.com`하며 *`appid`* 획득 링크와 `appid` 같아야 합니다. |
   | analytics | 테스트 목적을 위해 수동으로 브로드캐스트를 전송하는 데 적당한 시간(60초 이상)을 고려하도록 레퍼러 시간제한을 설정하십시오. 테스트 후 원래 시간제한 설정을 복원할 수 있습니다. |

1. 장치를 컴퓨터에 연결하고 앱을 제거한 다음 다시 설치합니다.
1. ADB 셸을 실행하고 장치에서 애플리케이션을 실행합니다.

   ```
   adb shell
   ```

1. 다음 `adb`명령을 사용하여 브로드캐스트를 전송합니다.

   ```
   am broadcast -a com.android.vending.INSTALL_REFERRER -n com.adobe.android/com.adobe.android.YourBroadcastReceiver --es "referrer" "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<unique id get on step 5>"
   ```

1. `com.adobe.android`를 애플리케이션의 패키지 이름으로, 수신자 참조를 앱 내의 캠페인 추적 수신자 위치로 바꾼 다음 `utm_content`}와 연결된 값을 바꿉니다.

   브로드캐스트가 성공하면 다음 예시와 같은 응답을 받게 됩니다.

   ```
   Broadcasting: Intent 
   { act=com.android.vending.INSTALL_REFERRER cmp=com.adobe.adms.tests/.ReferralReceiver (has extras) } 
   Broadcast completed: result=0 
   ```

1. (선택 사항) SDK의 디버그 로깅을 사용하여 추가 정보를 가져옵니다.

   모두 올바르게 작동하면 다음 로그가 표시됩니다.

   ```
   "Analytics - Received referrer information(<referrer content>)" 
   "Analytics - Trying to fetch referrer data from (acquisition end url)"; 
   "Analytics - Received Referrer Data(<A JSON Response>)"
   ```

   이 로그가 표시되지 않으면 6-10단계를 수행했는지 확인하십시오.

   발생할 수 있는 오류에 대한 추가 정보는 다음 표에 포함되어 있습니다.

   | 오류 | 설명 |
   |--- |--- |
   | Analytics - Unable to decode response(`<string>`). | 응답 형식이 잘못되었습니다. |
   | Analytics - Unable to parse response (`a JSON Response`). | JSON 문자열의 형식이 잘못되었습니다. |
   | Analytics - Unable to parse acquisition service response (no `contextData` parameter in response). | 응답에 `contextData` 매개 변수가 없습니다. |
   | Analytics - Acquisition referrer data was not complete (no `a.referrer.campaign.name` in context data), ignoring. | `a.referrer.campaign.name` 은 Contextdata에 포함되지 않습니다. |
   | Analytics - Acquisition referrer timed out. | `referrerTimeout`에 정의된 시간 내에 응답을 가져오지 못했습니다. 값을 늘린 다음 다시 시도하십시오.  또한 앱을 설치하기 전에 획득 링크를 열었는지 확인해야 합니다. |

다음 정보를 숙지하십시오.

* 앱에서 보낸 히트는 HTTP 모니터링 도구를 사용하여 획득 속성을 확인할 수 있도록 모니터링됩니다.
* `INSTALL_REFERRER`를 브로드캐스트하는 자세한 방법은 Google 개발자 가이드의 [Google Play 캠페인 측정 테스트](https://developers.google.com/analytics/solutions/testing-play-campaigns)를 참조하십시오.
* 제공된 `acquisitionTest.jar` Java 도구를 사용하여 고유 ID 및 브로드캐스트 설치 레퍼러를 가져와 3-10단계의 정보를 차례로 가져올 수 있습니다.

**Java 도구 설치**

Java 도구를 설치하려면

1. Download the [`acquistionTester.zip`](../assets/acquisitionTester.zip) file.
1. .jar 파일의 압축을 풉니다.

   명령줄에서 .jar 파일을 실행할 수 있습니다.

예:

```
java -jar acquisitionTester.jar -a com.adobe.test -r com.adobe.test.ReferrerReceiver -l "https://c00.adobe.com/v3/appid/start?a_i_id=123456&a_g_id=com.adobe.test&a_dd=i&ctxa.referrer.campaign.name=name&ctxa.referrer.campaign.trackingcode=1234
```

마케팅 링크는 10 분 만료 시간 동안 서버측에서 캐시됩니다. 표시 링크를 변경할 때 링크를 다시 사용하기 전에 변경 사항이 적용되도록 10분 정도 기다리십시오.