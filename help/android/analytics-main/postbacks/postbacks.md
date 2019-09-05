---
description: 포스트백을 사용하면 SDK에서 수집한 데이터를 타사 서버로 전송할 수 있습니다. 인앱 메시지를 표시하는 데 사용하는 것과 동일한 트리거와 트레이트를 이용하면 사용자 지정된 데이터를 타사 대상에 전송하도록 SDK를 구성할 수 있습니다.
keywords: Android; 라이브러리; 모바일; SDK
seo-description: 포스트백을 사용하면 SDK에서 수집한 데이터를 타사 서버로 전송할 수 있습니다. 인앱 메시지를 표시하는 데 사용하는 것과 동일한 트리거와 트레이트를 이용하면 사용자 지정된 데이터를 타사 대상에 전송하도록 SDK를 구성할 수 있습니다.
seo-title: 포스트백
solution: Marketing Cloud, Analytics
title: 포스트백 개요
topic: 개발자 및 구현
uuid: 8 BFD 4374-2767-421 D -891 D-E 1 E 9 A 99 B 6977
translation-type: tm+mt
source-git-commit: f26dcd5cf9b19de49c9d034c854d9738c7843fb2

---


# 포스트백 {#postbacks}

포스트백을 사용하면 SDK에서 수집한 데이터를 타사 서버로 전송할 수 있습니다. 인앱 메시지를 표시하는 데 사용하는 것과 동일한 트리거와 트레이트를 이용하면 사용자 지정된 데이터를 타사 대상에 전송하도록 SDK를 구성할 수 있습니다.

>[!IMPORTANT]
>
>이 기능을 사용하려면 SDK 4.6.0 이상이 필요합니다.

포스트백 메시지는 큐에 추가되고 분석 데이터 수집을 제어하는 기존의 모든 온라인/오프라인 규칙을 따릅니다. 표시된 메시지의 경우와 같이 메시지가 일치하면 포스트백 메시지는 나머지 메시지를 취소하지 않습니다. 이를 통해 동일한 분석 히트에서 포스트백이 여러 번 발생할 수 있습니다. 정의에 대한 내용은 *포스트백* 행( [ADBMobile JSON 구성](/help/android/configuration/json-config/json-config.md)을 참조하십시오.

## Template expansions {#section_6758AD05A24C4E9E965F5253294C164A}

Template expansions are available in the `templateurl` and `templatebody` properties. Template items take the form of `{key}`, where `key` is a context data key or traditional data key. The values that are available for template expansion are limited to the [Lifecycle metrics](/help/android/metrics.md), in addition to any custom data that is attached to the hit that triggers the message. 현재 사용할 수 있는 기록 기반 및 세그먼트 기반 데이터가 없습니다.

또한 특정 예약 템플릿은 SDK에 알려진 내부 데이터로 자동 대체됩니다.

이 목록에는 다음이 포함됩니다.

| 토큰 이름 | 토큰 설명 |
|--- |--- |
| {%sdkver%} | SDK 버전을 반환합니다. |
| {%cachebust%} | 1에서 100000000 사이의 임의의 숫자로 확인됩니다. |
| {%adid%} | Android용 광고주 ID를 반환합니다. 참고: 이 템플릿은 `submitAdvertisingIdentifierTask`를 사용한 경우에만 작동합니다. |
| {%pushid%} | 푸시 식별자 토큰을 반환합니다. 참고: 이 템플릿은 `setPushIdentifier`를 사용한 경우에만 작동합니다. |
| {%timestampu%} | epoch 시간의 현재 타임스탬프를 반환합니다. |
| {%timestampz%} | 현재 타임스탬프를 JavaScript(ISO 8601) 형식으로 반환합니다. |