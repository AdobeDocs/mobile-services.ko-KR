---
description: .xml 파일을 직접 대체하여 TVMLTVJS 앱에서 Adobe Target을 활용할 수 있습니다. 사용자 지정 ADBTarget XML 요소를 사용하여 타겟 콘텐츠에서 대체할 페이지 영역을 지정하십시오.
seo-description: .xml 파일을 직접 대체하여 TVMLTVJS 앱에서 Adobe Target을 활용할 수 있습니다. 사용자 지정 ADBTarget XML 요소를 사용하여 타겟 콘텐츠에서 대체할 페이지 영역을 지정하십시오.
seo-title: TVML/TVJS용 Adobe Target
title: TVML/TVJS용 Adobe Target
uuid: AFD 5 A 583-5266-43 F 2-8 CB 0-0 ACE 89 C 53 A 57
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# TVML/TVJS용 Adobe Target{#adobe-target-for-tvml-tvjs}

.xml 파일을 직접 대체하여 TVMLTVJS 앱에서 Adobe Target을 활용할 수 있습니다. 사용자 지정 ADBTarget XML 요소를 사용하여 타겟 콘텐츠에서 대체할 페이지 영역을 지정하십시오.

>[!IMPORTANT]
>
>Before using the `ADBTarget` element in your TVML pages, you must configure your TVML/TVJS app to use the tvOS SDK. 자세한 내용은 Tvos를 사용한 [Apple TV 구현을 참조하십시오](/help/ios/apple-tv-implementation-tvos/apple-tv-implementation-tvos.md).

## 시작하기 {#section_88445645FD67416EAF6FDC3E3D3F5C33}

1. Identify the `.xml` file in which you want to use your Target location.
1. Add an `ADBTarget` element to the file as a child of the `<document>` element.
1. If Target fails to find your Mbox location, or it times out, the value between your `<ADBTarget>` and `</ADBTarget>` tags is used as default content.

## Configure your mbox in Target {#section_F2DA140C34B0421D976046F825B23123}

The returned content from Target replaces all content between `<ADBTarget>` and `</ADBTarget>`, including both `ADBTarget` tags.

>[!TIP]
>
>대체할 항목을 계획해야 합니다.

사용 사례는 레이블의 문자열 값을 대체하는 것처럼 간단하거나, 페이지 전체를 대체하는 것처럼 복잡할 수도 있습니다.

## Adbtarget 요소 구성 {#section_44A7AEC6FC0648ADAD0BACB57D493AFA}

`ADBTarget` 요소에서 `mbox` 속성에 Mbox 이름을 제공해야 합니다. You can optionally add custom properties to your request in the `customParameterName="customParameterValue"` format.

* **`mbox`**

   Mbox 위치 이름.

   * 속성 유형: 문자열
   * 이 속성은 필수입니다.

* **`id`**

   주문 ID.

   * 속성 유형: 문자열
   * 이 **속성은** 필수가 아닙니다.

* **`total`**

   주문 합계.

   * 속성 유형: 문자열
   * 이 **속성은** 필수가 아닙니다.

* **`purchasedProductIds`**

   이 주문에 대해 구입한 제품 ID를 쉼표로 구분한 목록입니다.

   * 다음은 이 속성의 코드 샘플입니다.


      ```objective-c
      purchasedProductIds="product1,product2,product3" 
      ```

   * 속성 유형: 문자열
   * 이 **속성은** 필수가 아닙니다.

* **`mboxParameters`**

   `mboxParameters`의 키 값 쌍 목록입니다. 이 문자열의 각 항목은 세미콜론으로 구분하고 키 값은 콜론으로 구분됩니다.

   * 다음은 이 속성의 코드 샘플입니다.

      ```objective-c
      mboxParameters="mboxparameterKey:mboxParameterValue;mboxParameterKey1:mboxParameterValue1;mboxParameterKey2:mboxParameterValue2"
      ```

   * 속성 유형: 문자열
   * 이 **속성은** 필수가 아닙니다.

* **`customParameterName`**

   이 속성의 값은 `customParameterValue`입니다.

   * 속성 유형: 문자열
   * 이 **속성은** 필수가 아닙니다.


## 예 {#section_6D6D6E8C7FE147168FC30D83CBC06985}

### 예제 1

다음 예에서는 `ADBTarget` 페이지의 `LandingPage.xml.js` 요소를 사용하여 경고 내용을 바꿉니다.

#### 타겟 구성

`landingPage`라는 이름의 Mbox 위치가 있고 오퍼 콘텐츠가 다음과 같이 설정되어 있다고 가정합니다.

```objective-c
<title>My cool landing page</title> 
<description>Thanks for coming to my page</description> 
```

#### landingPage.xml.js 구성

* landingPage.xml.js의 구성은 다음과 같습니다.

   ```js
   <alertTemplate> 
       <ADBTarget mbox="landingPage">  
           <title>TargetTestPage</title> 
           <description>Load fail or timeout (defaultContent)</description> 
       </ADBTarget>  
   </alertTemplate> 
   ```

* 타겟에 대한 요청이 성공하고 주문 내용이 반환되었을 경우 페이지의 결과는 다음과 같습니다.

   ```objective-c
   <alertTemplate> 
       <title>My cool landing page</title> 
       <description>Thanks for coming to my page</description> 
   </alertTemplate>
   ```

* Target 서버에 연결할 수 없거나 요청 시간이 초과되었을 경우 페이지의 결과는 다음과 같습니다.

   ```objective-c
   <alertTemplate> 
       <title>TargetTestPage</title> 
       <description>Load fail or timeout (defaultContent)</description> 
   </alertTemplate>
   ```

### 예제 2

다음 예에서는 `ADBTarget` 요소에 사용자 지정 데이터를 추가하는 방법을 보여줍니다. 이 메서드를 사용하면 조건부 환경을 만들고 타겟에서 이 Mbox 위치에 대한 콘텐츠를 제공할 수 있습니다.

```objective-c
<alertTemplate> 
    <ADBTarget mbox="landingPage" customData="custom data" moreCustomData="more custom data"> 
        <title>TargetTestPage</title> 
        <description>Load fail or timeout (defaultContent)</description> 
    </ADBTarget>  
</alertTemplate>
```