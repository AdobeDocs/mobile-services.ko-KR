---
description: Adobe Mobile 및 Adobe Mobile SDK를 사용하면 사용자에게 푸시 메시지를 보낼 수 있습니다. 또한 SDK를 사용하면 푸시 메시지를 클릭스루하여 앱을 열어 본 사용자를 쉽게 보고할 수도 있습니다.
seo-description: Adobe Mobile 및 Adobe Mobile SDK를 사용하면 사용자에게 푸시 메시지를 보낼 수 있습니다. 또한 SDK를 사용하면 푸시 메시지를 클릭스루하여 앱을 열어 본 사용자를 쉽게 보고할 수도 있습니다.
seo-title: 푸시 메시지
solution: Marketing Cloud, Analytics
title: 푸시 메시지
topic: 개발자 및 구현
uuid: 729 D 4010-3733-4 DFF-B 188-AD 45 BD 3 E 7 CC 4
translation-type: tm+mt
source-git-commit: 17cb91a28966cf32f955a2cb724e89ab228de5b8

---


# Push messaging {#push-messaging}

Adobe Mobile 및 Adobe Mobile SDK를 사용하면 사용자에게 푸시 메시지를 보낼 수 있습니다. 또한 SDK를 사용하면 푸시 메시지를 클릭스루하여 앱을 열어 본 사용자를 쉽게 보고할 수도 있습니다.

푸시 메시지를 사용하려면 **반드시** SDK 버전 4.6 이상이 있어야 합니다.

>[!IMPORTANT]
>
>앱 내에서 Experience Cloud ID를 수동으로 설정하지 마십시오. 이렇게 하면 옵트인 상태로 인해 푸시 메시지를 수신하지 않는 고유 사용자가 새로 생성됩니다. 예를 들어 푸시 메시지를 수신하도록 옵트인한 사용자가 앱에 로그인합니다. 로그인한 후 앱에서 ID를 수동으로 설정하면 푸시 메시지를 수신하지 않도록 선택한 고유 사용자가 새로 만들어집니다. 이 새로운 사용자는 푸시 메시지를 수신하지 않습니다.
>
>앱을 새 보고서 세트로 이동하는 것은 지원되지 않습니다. 새 보고서 세트로 마이그레이션하는 경우 푸시 구성이 중단되고 메시지가 전송되지 않을 수 있습니다.

## Enable push messaging {#section_CBD63C5B11FE4424BC2BF552C23F2BD9}

>[!TIP]
>
>앱이 이미 Firebase 클라우드 메시지 (FCM) 를 통해 메시지를 사용하도록 설정되어 있는 경우 다음 단계 중 일부가 이미 완성될 수 있습니다.

1. `ADBMobileConfig.json` 파일에 푸시 메시지에 대한 필수 설정이 포함되어 있는지 확인합니다.

   `"marketingCloud"` 개체에 푸시 메시징을 `"org"` 위해 속성이 구성되어 있어야 합니다.

   ```js
   "marketingCloud": { 
     "org": <org-id-string> 
    }
   ```

1. Firebase Cloud Messaging(FCM) API를 사용하여 등록 ID/토큰을 얻습니다.

   * FCM 설정에 대한 자세한 내용은 [Android용 Firebase Cloud 메시지 클라이언트 앱 설정](https://firebase.google.com/docs/cloud-messaging/android/client)을 참조하십시오.
   ```js
   String token = FirebaseInstanceId.getInstance().getToken();
   ```

1. The registration ID/token must be passed to the SDK by using the `Config.setPushIdentifier(final String registrationId)` method.

   ```js
   Config.setPushIdentifier(token); // token was obtained in step 2
   ```

1. `collectLifecycleData` 메서드의 활동을 전달하여 보고 기능을 활성화합니다.

   푸시 클릭스루 보고 기능을 활성화하기 위한 요구 사항은 다음과 같습니다.

   * In your implementation of `FireBaseMessageService`, the Bundle object that contains the message data, which is passed into the `onMessageReceived` method with the RemoteMessage object, must be added to the Intent that is used to open the target activity on a click-through. 이 작업은 `putExtras` 메서드를 사용하여 수행할 수 있습니다. 자세한 내용은 [Putextras](https://developer.android.com/reference/android/content/Intent.html#putExtras(android.os.Bundle))를 참조하십시오.
   ```java
   Intent intent = new Intent(this, MainActivity.class);
      intent.addFlags(Intent.FLAG_ACTIVITY_CLEAR_TOP);
   // get the bundle from the RemoteMessage object
      intent.putExtras(message.toIntent().getExtras());
   ```

   * 클릭스루 타겟 활동에서 `collectLifecycleData` 호출을 사용하여 해당 활동을 SDK에 전달해야 합니다.

      다음 정보를 숙지하십시오.

      * 사용 `Config.collectLifecycleData(this)` 또는 `Config.collectLifecycleData(this, contextData)`.

      * ****`Config.collectLifecycleData()`사용하지 마십시오.


