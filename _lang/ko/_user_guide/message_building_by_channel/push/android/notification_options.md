---
nav_title: "알림 옵션"
article_title: Android 알림 옵션
page_order: 2
page_type: reference
description: "이 참고 문서에서는 몇 가지 안드로이드 알림 옵션과 Braze 캠페인 내에서 이를 가장 효과적으로 사용하는 방법에 대해 설명합니다."

platform: Android
channel:
  - Push

---

# 알림 옵션

> 메시지를 분류하여 사용자의 알림 트레이에 그룹화하려면 Braze를 통해 안드로이드의 알림 채널 기능을 활용할 수 있습니다.

Android 푸시 캠페인을 만든 다음 **작성** 탭 상단에서 **알림 채널** 드롭다운을 찾습니다.

![][28]{: style="max-width:60%;" }

드롭다운에서 알림 채널을 선택합니다. 또한 알림 채널 설정이 오작동하는 경우를 대비하여 대체 채널을 선택해야 합니다.

여기에 나열된 [알림 채널이]({{site.baseurl}}/user_guide/message_building_by_channel/push/android/notification_channels/) 없는 경우 알림 채널 ID를 사용하여 알림 [채널을]({{site.baseurl}}/user_guide/message_building_by_channel/push/android/notification_channels/) 추가할 수 있습니다. 개발자에게 문의하여 알림 채널 ID가 무엇인지 확인하거나 필요에 따라 새 ID를 만들 수 있습니다. 

알림 채널에 알림 ID를 추가하려면 **알림 채널** 드롭다운 메뉴에서 **알림** **채널 관리를** 클릭하고 필수 입력란을 작성합니다. 알림 채널은 앱에서 정의해야만 Braze 플랫폼에서 사용할 수 있습니다.

![][29]{: style="max-width:80%;" }


[28]: {% image_buster /assets/img_archive/notification_channel_dropdown.png %}
[29]: {% image_buster /assets/img_archive/notification_channels.png %}
