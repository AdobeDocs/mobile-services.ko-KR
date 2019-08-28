---
product: 모바일 서비스
audience: 최종 사용자
user-guide-title: Mobile Services iOS 도움말
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Mobile Services iOS 도움말 {#ios}

+ [Experience Cloud 솔루션용 iOS SDK 4.x](overview.md)
+ [릴리스 노트](rel-notes.md)
+ 시작하기 {#getting-started-ios}
   + [시작하기 개요](getting-started/getting-started.md)
   + [시작하기 전에](getting-started/requirements.md)
   + [핵심 구현 및 라이프사이클](getting-started/dev-qs.md)
   + [처리 규칙 및 컨텍스트 데이터](getting-started/proc-rules.md)
   + [Swift 통합](getting-started/swift-integration.md)
   + [4. x iOS 라이브러리로 마이그레이션](getting-started/migration-v3.md)
+ 구성 {#config-ios}
   + [구성 개요](configuration/configuration.md)
   + [Adbmobile JSON 구성](configuration/json-config/json-config.md)
   + [Adbmobile JSON 구성 경로 재정의](configuration/json-config/json-config-remote.md)
   + [히트 배치 처리](configuration/hit-batching.md)
   + [구성 메서드](configuration/sdk-methods.md)
   + [앱 전송 보안](configuration/app-transport-security.md)
+ [라이프사이클 지표](metrics.md)
+ Analytics {#analytics-ios}
   + [분석 개요](analytics-main/analytics-main.md)
   + [앱 상태 추적](analytics-main/states.md)
   + [앱 작업 추적](analytics-main/actions.md)
   + [앱 충돌 추적](analytics-main/crashes.md)
   + [시간 제한 작업](analytics-main/timed-actions.md)
   + [방문자 라이프타임 값](analytics-main/lifetime-value.md)
   + Products variable {#products-variable}
      + [제품 변수](analytics-main/products/products.md)
      + [머천다이징 Evar 및 제품별 이벤트를 포함한 제품 변수](analytics-main/products/products-variable-evars-events.md)
   + [이벤트 정리](analytics-main/event-serialization.md)
   + [Video Analytics](analytics-main/video-qs.md)
   + 포스트백 {#postbacks}
      + [포스트백 개요](analytics-main/postback/postback.md)
      + [포스트백 예](analytics-main/postback/postback-example.md)
      + [PII 포스트백](analytics-main/postback/c-pii-postbacks.md)
   + [Analytics 메서드](analytics-main/analytics-methods.md)
+ 획득 {#acquisition-ios}
   + [고객 확보 개요](acquisition-main/acquisition-main.md)
   + [모바일 앱 확보](acquisition-main/acquisition.md)
   + [획득 방법](acquisition-main/c-acquisition-methods.md)
   + Tracking deep links {#tracking-deep-links}
      + [딥 링크 추적](acquisition-main/tracking-deep-links/tracking-deep-links.md)
      + [타사 지연된 딥 링크 추적](acquisition-main/tracking-deep-links/c-tracking-3rd-party-deep-deferred-links.md)
   + [마케팅 링크 획득 테스트](acquisition-main/t-testing-marketing-link-acquisition.md)
   + [v 3 확보 테스트](acquisition-main/t-testing-version-3-acquisition.md)
   + [기존 확보 테스트](acquisition-main/t-testing-acquisition.md)
   + [Apple 검색 광고](acquisition-main/c-apple-search-ads.md)
+ 메시징 {#messaging-ios}
   + [메시징 개요](messaging-main/messaging-main.md)
   + 인앱 메시징 {#in-app-messaging}
      + [인앱 메시징](messaging-main/messaging/messaging.md)
      + [인앱 메시지 문제 해결](messaging-main/messaging/in-apps-ts.md)
   + Push messaging {#push-messaging}
      + [푸시 메시지](messaging-main/push-messaging/push-messaging.md)
      + [딥 링크를 사용하여 푸시 메시지 구현](messaging-main/push-messaging/t-mob-imp-push-deeplinking-ios-4x.md)
      + [풍부한 푸시 알림 받기](messaging-main/push-messaging/c-set-up-rich-push-notif-ios.md)
      + [푸시 메시지 문제 해결](messaging-main/push-messaging/c-troubleshooting-push-messaging.md)
+ 위치 {#location-ios}
   + [위치 개요](location/location.md)
   + [지리적 위치 및 관심 영역](location/geo-poi.md)
   + [iBeacon 추적](location/ibeacon.md)
+ Target {#target-ios}
   + [Target 개요](target-main/target-main.md)
   + [Target 메서드](target-main/c-target-methods.md)
   + [iOS에서 오퍼 컨텐츠 미리 가져오기](target-main/c-mob-target-prefetch-ios.md)
   + [iOS에서 타겟 미리 보기](target-main/c-mob-target-preview-ios.md)
+ Experience Cloud {#exp-cloud-ios}
   + [Experience Cloud 개요](marketing-cloud/marketing-cloud.md)
   + [Experience Cloud ID](marketing-cloud/mcvid.md)
   + [Adobe Experience Platform Identity Service 방식](marketing-cloud/mc-methods.md)
   + [Experience Cloud Device Co-op](marketing-cloud/t-mob-mc-device-coop-ios-.md)
+ [Audience Manager 메서드](amm/aam-methods.md)
+ Apple TV implementation with tvOS {#apple-tv-implementation-tvos-ios}
   + [Tvos를 사용한 Apple TV 구현](apple-tv-implementation-tvos/apple-tv-implementation-tvos.md)
   + [TVML/TVJS용 Adobe Target](apple-tv-implementation-tvos/target-for-tvml-tvjs.md)
   + [TVJS 메서드](apple-tv-implementation-tvos/tvjs-methods.md)
+ iOS extension implementation {#ios-ext}
   + [iOS 확장 구현](ios-ext/ios-ext.md)
   + [독립 실행형 확장 구현](ios-ext/c-stand-alone-extension-implementation.md)
+ [Watchos 2를 사용한 Apple Watch 구현](apple-watch-implementation-watchkit.md)
+ iOS SDK reference {#sdk-reference-ios}
   + [iOS SDK 참조](reference/reference.md)
   + [앱 ID](reference/app-ids.md)
   + [앱과 모바일 웹 간 방문자 추적](reference/hybrid-app.md)
   + [iOS 디바이스 버전](reference/device-versions.md)
+ 개인 정보 및 일반 데이터 보호 규정{#privacy-gdpr-ios}
   + [개인 정보 및 일반 데이터 보호 규정](c-mob-privacy-gdpr-ios/c-mob-privacy-gdpr-ios.md)
   + [저장된 식별자 검색](c-mob-privacy-gdpr-ios/c-mob-gdpr-ret-stored-ids-ios.md)
   + [사용자의 선택 상태 설정](c-mob-privacy-gdpr-ios/privacy.md)
+ PhoneGap 플러그인 {#phonegap-ios}
   + [Phonegap 플러그인](phonegap/phonegap.md)
   + [Phonegap 플러그인 메서드](phonegap/phonegap-methods.md)