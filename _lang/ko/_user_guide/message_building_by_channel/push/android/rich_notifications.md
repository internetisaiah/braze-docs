---
nav_title: "Android 리치 알림"
article_title: Android용 리치 알림
page_order: 3
page_layout: tutorial
description: "이 튜토리얼에서는 Braze 캠페인에 대한 Android 리치 알림 설정 방법을 다룹니다."
platform: Android
channel:
  - Push
tool:
  - Campaigns
  
---

# Android 리치 알림

> 리치 알림은 단순한 복사본 이상의 추가 콘텐츠를 추가하여 푸시 알림을 더 맞춤화할 수 있게 해줍니다. Android 알림에는 푸시 알림에 이미지가 포함된 지 오래되었으며, 이를 "확장된 알림 이미지"라고 합니다.

## 요구 사항

- Android 리치 알림은 퀵 푸시 캠페인을 만들 때 사용할 수 없습니다.
- 확장된 알림 보기 기능은 Jelly Bean (Android 4.1) 이상을 사용하는 기기에서만 사용할 수 있습니다. 사용자의 기기가 이러한 시스템에서 실행되지 않으면 알림 이미지를 볼 수 없습니다.
- Android 확장 알림 이미지의 비율은 2:1이어야 하지만, 크기 제한은 없습니다.
- Android 또한 표준 알림 보기에서 별도의 이미지를 설정할 수 있습니다. 다음은 권장 크기 이미지입니다: 
  - 작은: 512x256
  - 중간: 1024x512 
  - 큰: 2048x1024
- 현재 Android 리치 알림은 JPEG 및 PNG 이미지 형식을 포함한 정적 이미지 만 허용합니다. GIF 및 기타 이미지 형식은 아직 지원되지 않습니다.
- 푸시 알림에 작업 버튼을 추가하면 표시할 수 있는 이미지 영역에 영향을 미칠 수 있습니다. 대시보드 미리보기 및 실시간 장치를 사용하여 결과가 예상대로인지 확인하십시오.

{% alert note %}
Braze는 리치 푸시 설정 방법에 대한 지침을 제공하지만, 리치 푸시 알림의 실제 렌더링은 기기 종횡비, Android 버전, OEM별 제약 조건 등 외부 요인에 따라 달라질 수 있습니다. 여러 Android 기기에 전송 테스트를 수행하여 리치 푸시 알림이 의도한 대로 표시되는지 확인하는 것이 좋습니다.
{% endalert %}

## Android 리치 알림 설정

### 1단계: 캠페인을 만들기

단계를 따라 [캠페인을 생성][3]하여 Android용 푸시 알림을 작성하세요. 푸시 알림을 설정할 때 동일한 작곡가를 사용하게 됩니다. 이 알림에는 풍부한 콘텐츠가 포함되지 않습니다.

### 2단계: 자막 추가

알림에서 이미지 앞에 표시할 **요약 텍스트/이미지 캡션**을 추가합니다.

![][9]

### 3단계: 미디어 추가

메시지의 작성기에서 **확장된 알림 이미지** 필드에 이미지를 추가하세요. 이미지는 대시보드를 통해 직접 업로드하거나 다른 곳에 호스팅된 콘텐츠 URL을 지정하여 업로드할 수 있습니다.

자세한 내용은 [이미지 사양]({{site.baseurl}}/user_guide/engagement_tools/templates_and_media/media_library/#push)을 확인하세요.

![][8]

### 4단계: 캠페인을 계속 만드세요

리치 알림 콘텐츠가 대시보드에 업로드된 후, [캠페인을 예약][6]할 수 있습니다.

[3]: {{site.baseurl}}/user_guide/message_building_by_channel/push/creating_a_push_message/#creating-a-push-message
[6]: {{site.baseurl}}/user_guide/engagement_tools/campaigns/scheduling_and_organizing/delivery_types/
[8]: {% image_buster /assets/img_archive/android_rich_image.png %}
[9]: {% image_buster /assets/img_archive/android_rich_summarytext.png %}
