---
description: 다음 지침은 장치 지문을 기반으로 하는 마케팅 링크를 사용하여 획득 캠페인을 라운드트립 하는 데 도움이 됩니다.
keywords: Android; 라이브러리; 모바일; SDK
seo-description: 다음 지침은 장치 지문을 기반으로 하는 마케팅 링크를 사용하여 획득 캠페인을 라운드트립 하는 데 도움이 됩니다.
seo-title: 마케팅 링크 획득 테스트
solution: Marketing Cloud, Analytics
title: 마케팅 링크 획득 테스트
topic: 개발자 및 구현
uuid: 69503 E 01-182 D -44 C 6-B 0 FB-E 1 C 012 FFA 3 BD
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Testing Marketing Link acquisition {#testing-marketing-link-acquisition}

다음 지침은 장치 지문을 기반으로 하는 마케팅 링크를 사용하여 획득 캠페인을 라운드트립 하는 데 도움이 됩니다.

1. 모바일 앱 확보에서 [전제 조건 작업을 완료합니다](/help/ios/acquisition-main/acquisition.md).
1. In the Adobe Mobile Services UI, click **[!UICONTROL Marketing Links Builder]** and generate an acquisition Marketing Link URL that sets the App Store as the destination for iOS devices.

   예:

   ```
   https://c00.adobe.com/v3/da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d/start?a_dl=57477650072932ec6d3a470f
   ```

   자세한 정보는 [마케팅 링크 빌더](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md)를 참조하십시오.


1. Open the generated link on the iOS device and open `https://c00.adobe.com/v3/<appid>/end`.

   다음과 같이 JSON 응답에 contextData가 표시되어야 합니다.

   ```js{"fingerprint":"bae91bb778f0ad52e37f0892961d06ac6a5c935b","endCallbacks":["***"],"timestamp":1464301217,"appguid":"da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d","contextData":
   {"a.launch.campaign.trackingcode":"twdf4546","a.referrer.campaign.name":"iOS Demo","a.referrer.campaign.trackingcode":"twdf4546"}
   ,"adobeData":{"unique_id":"8c14098d7c79e8a180c15e4b2403549d3cc21ea8","deeplinkid":"57477650072932ec6d3a470f"}}
   ```

1. 구성 파일에서 다음 설정이 올바른지 확인합니다.

   | 이 예에서 | 값 |
   |--- |--- |
   | acquisition | `c00.adobe.com`서버가 있어야 합니다. `appid` 의 값은 획득 *`appid`* 링크와 같아야 합니다. |
   | analytics | `referrerTimeout` 값은 0보다 커야 합니다. |

1. (선택 사항) 앱 구성 파일의 SSL 설정이`false`일 경우 HTTPS 대신 HTTP 프로토콜을 사용하도록 획득 링크를 업데이트합니다.
1. 앱을 설치하려는 모바일 장치에서 생성된 링크를 클릭합니다.

   Adobe 서버(`c00.adobe.com`)는 지문 파일을 저장한 다음 앱스토어로 리디렉션합니다. 테스트를 위해 앱을 다운로드할 필요는 없습니다.
1. 6단계에서 사용한 것과 동일한 모바일 장치에서 처음으로 애플리케이션을 시작합니다.

   필요한 경우 앱을 삭제하고 다시 설치할 수 있습니다.
1. (선택 사항) SDK의 디버그 로깅을 사용하여 추가 정보를 얻습니다.

   모두 올바르게 작동하면 다음 로그가 표시됩니다.

   `"Analytics - Trying to fetch referrer data from <acquisition end url>"`
   `"Analytics - Received Referrer Data(<Json Object>)"`

   이러한 로그가 표시되지 않으면 4 단계와 5 단계를 완료했는지 확인하십시오.

   다음은 가능한 오류에 대한 정보입니다.

   * `Analytics - Unable to retrieve acquisition service response (<error message>)`:

      네트워크 오류가 발생했습니다.

   * `Analytics - Unable to parse acquisition service response (<error message>)`

      응답 형식이 올바르지 않습니다.

   * `Analytics - Unable to parse acquisition service response (no contextData parameter in response)`

      응답에 `contextData` 매개 변수가 없습니다.

   * `Analytics - Acquisition referrer data was not complete, ignoring`

      `a.referrer.campaign.name``contextData`에 포함되어 있지 않습니다.

   * `Analytics - Acquisition referrer timed out`

      `referrerTimeout`에 정의된 시간 내에 응답을 가져오지 못했습니다. 값을 늘린 다음 다시 시도하십시오. 또한 앱을 설치하기 전에 획득 링크를 열었는지, URL을 클릭해서 앱을 열 때 동일한 네트워크를 사용했는지 확인해야 합니다.

다음 정보를 숙지하십시오.

* 획득 서버는 링크 클릭(6단계) 및 앱 실행(7단계)에 기록된 IP 주소 및 사용자 에이전트 정보를 기반으로 속성 일치를 제공합니다.

   URL을 클릭할 때와 앱을 열 때 동일한 네트워크에 있어야 합니다.

* HTTP 모니터링 도구를 사용하면 앱에서 전송된 히트를 모니터링하여 획득 속성을 확인할 수 있습니다.

   You should see one `/v3/<appid>/start` request and one `/v3/<appid>/end` request that are sent to the acquisition server.

* 전송된 사용자 에이전트의 변형으로 인해 속성 확인이 실패할 수 있습니다.

   동일한 사용자 에이전트 값을 `https://c00.adobe.com/v3/<appid>/start` 가지고 `https://c00.adobe.com/v3/<appid>/end` 있어야 합니다.

* 획득 링크와 SDK의 히트는 동일한 HTTP/HTTPS 프로토콜을 사용해야 합니다.

   링크와 히트가 서로 다른 프로토콜을 사용하는 경우, 예를 들어 링크가 HTTP를 사용하고 SDK가 HTTPS를 사용하는 경우 IP 주소가 각 요청마다 일부 통신사에 따라 다를 수 있습니다. 이로 인해 속성 확인이 실패할 수 있습니다.

* 마케팅 링크는 10 분 만료 시간 동안 서버측에서 캐시됩니다.

   마케팅 링크를 변경하는 경우 링크를 사용하기 전에 약 10 분 정도 기다려야 합니다.