---
nav_title: 사용자 데이터 및 CSV 이벤트 가져오기
article_title: 사용자 데이터 및 CSV 이벤트 가져오기
permalink: "/csv_events/"
description: "이 참고 문서에서는 사용자 데이터를 가져오는 방법과 CSV 파일을 사용하여 커스텀 이벤트를 가져오는 방법에 대해 설명합니다."
page_type: reference
---

# 사용자 데이터 가져오기(CSV 이벤트 미리 보기)

> Braze는 사용자 데이터를 플랫폼으로 가져올 수 있는 다양한 방법을 제공합니다. 바로 SDK, API, 클라우드 데이터 수집, 기술 파트너 통합 및 CSV 파일입니다. 이 글에서는 [CSV 파일을 통해 커스텀 이벤트를 가져오는](#importing-custom-events) 방법(얼리 액세스)를 포함하여 사용자 데이터를 가져오는 방법에 대한 자세한 지침을 제공합니다.

{% multi_lang_include email-via-sms-warning.md %}

계속 진행하기 전에, Braze는 가져오는 동안 HTML 데이터를 정리(유효성 검사 또는 적절한 형식 지정)하지 않는다는 점에 유의하세요. 즉, 웹 개인화를 위한 모든 가져오기 데이터에서 스크립트 태그를 제거해야 합니다.

## REST API

[`/users/track` 엔드포인트를]({{site.baseurl}}/api/endpoints/user_data/post_user_track/) 사용하여 커스텀 이벤트, 커스텀 속성 및 사용자에 대한 구매를 기록할 수 있습니다.

## CSV 가져오기

**오디언스** > **사용자 가져오기**에서 CSV 파일을 통해 고객 프로필을 업로드하고 업데이트할 수 있습니다.

CSV 파일을 사용하여 사용자 데이터를 가져오면 신발 사이즈와 같은 커스텀 속성뿐만 아니라 이름, 이메일과 같은 사용자 속성의 기록 및 업데이트가 지원됩니다. `external_id` 또는 사용자 별칭의 두 가지 고유 사용자 식별자 중 하나를 지정하여 CSV를 가져올 수 있습니다.

{% alert important %}
사용자 가져오기는 사용자 사용자 지정 이벤트 기록 및 업데이트도 지원합니다. 사용자 속성과 마찬가지로 `external_id`, `braze_id` 또는 `user_alias_label`이 있는 `user_alias_name`을 사용하여 가져올 수 있습니다. 자세한 내용은 [사용자 지정 이벤트 가져오기를](#importing-custom-events) 참조하세요.
{% endalert %}

{% alert note %}
`external_id` 주소가 있는 사용자와 없는 사용자를 혼합하여 업로드하는 경우 각 가져오기마다 하나의 CSV 파일을 만들어야 합니다. 하나의 CSV 파일에는 `external_ids` 및 사용자 별칭을 모두 포함할 수 없습니다.
{% endalert %}

### 외부 ID로 가져오기

고객 데이터를 가져올 때 각 고객의 고유 식별자(`external_id`)를 지정해야 합니다. CSV 가져오기를 시작하기 전에 엔지니어링 팀으로부터 Braze에서 사용자를 식별하는 방법을 이해하는 것이 중요합니다. 일반적으로 내부 데이터베이스 ID입니다. 이는 모바일과 웹에서 Braze SDK가 사용자를 식별하는 방식과 일치해야 하며 각 고객이 여러 기기에서 Braze 내에서 단일 고객 프로필을 가질 수 있도록 설계되었습니다. Braze에 대해 자세히 알아보세요. \[사용자 프로필 수명주기][13].

가져오기에 `external_id` 을 입력하면 Braze는 기존 사용자를 동일한 `external_id` 으로 업데이트하거나, 사용자를 찾을 수 없는 경우 해당 `external_id` 설정으로 새로 식별된 사용자를 생성합니다.

- **다운로드:** \[CSV 속성 가져오기 템플릿]\[import_template]
- **다운로드:** \[CSV 이벤트 가져오기 템플릿]\[events_template]

### 사용자 별칭으로 가져오기

`external_id`가 없는 사용자를 타겟팅하려면 사용자 별칭이 있는 사용자 목록을 가져올 수 있습니다. 별칭은 대체 고유 사용자 식별자 역할을 하며, 앱에 가입하거나 계정을 만들지 않은 익명 사용자를 대상으로 마케팅하려는 경우 유용할 수 있습니다.

별칭만 있는 사용자 프로필을 업로드하거나 업데이트하는 경우 CSV에 다음 두 개의 열이 있어야 합니다:

- `user_alias_name`: 고유한 사용자 식별자이자 `external_id`의 대안
- `user_alias_label`: 사용자 별칭을 그룹화할 수 있는 공통 레이블

| user_alias_name | user_alias_label | last_name | 이메일 | sample_attribute |
| --- | --- | --- | --- | --- |
| 182736485 | my_alt_identifier | Smith | smith@user.com | TRUE |
| 182736486 | my_alt_identifier | Nguyen | nguyen@user.com | FALSE |
{: .reset-td-br-1 .reset-td-br-2 .reset-td-br-3  .reset-td-br-4}

가져오기에 `user_alias_name` 및 `user_alias_label` 모두 제공하면 Braze는 기존 사용자를 동일한 `user_alias_name` 및 `user_alias_label`로 업데이트합니다. 사용자를 찾을 수 없는 경우, Braze는 해당 `user_alias_name` 설정으로 새로 식별된 사용자를 생성합니다.

{% alert important %}
기존 사용자에게 이미 `external_id`가 있는 경우 CSV 가져오기를 사용하여 `user_alias_name`가 있는 사용자를 업데이트할 수 없습니다. 대신 `user_alias_name`에 연결된 새 고객 프로필이 생성됩니다. 별칭 전용 사용자를 `external_id`에 연결하려면 [사용자 식별 엔드포인트]({{site.baseurl}}/api/endpoints/user_data/post_user_identify/)를 사용합니다.
{% endalert %}

- **다운로드:** \[CSV 별칭 속성 가져오기 템플릿]\[template_alias_attributes]
- **다운로드:** \[CSV 별칭 이벤트 가져오기 템플릿]\[template_alias_events]

### Braze ID로 가져오기

`external_id` 또는 `user_alias_name`, `user_alias_label` 값 대신 내부 Braze ID 값을 사용하여 기존 고객 프로필을 업데이트하려면 열 헤더로 `braze_id`를 지정하세요.

이는 세분화 내의 CSV 내보내기 옵션을 통해 Braze에서 사용자 데이터를 내보낸 후 기존 사용자에게 새로운 사용자 지정 속성을 추가하려는 경우에 유용할 수 있습니다.

{% alert important %}
`braze_id`를 사용하여 새 사용자를 만드는 데는 CSV 가져오기를 사용할 수 없습니다. 이 방법은 Braze 플랫폼 내에서 기존 사용자를 업데이트하는 데에만 사용할 수 있습니다.
{% endalert %}

{% alert tip %}
Braze 대시보드의 CSV 내보내기에서 `braze_id` 값은 `Appboy ID`로 레이블이 지정될 수 있습니다. 이 ID는 사용자의 `braze_id`와 동일하므로 CSV를 다시 가져올 때 이 열의 이름을 `braze_id`로 변경할 수 있습니다.
{% endalert %}

### 기본 속성 가져오기

사용자에 대한 기본 속성을 가져오려면 사용자 **가져오기** > **속성**으로 이동합니다. 기본 사용자 속성은 Braze의 예약 키입니다. 예: `first_name` 또는 `email`. 사용자 지정 속성은 비즈니스에 맞게 설정할 수 있습니다. 예를 들어 여행 예약 앱에는 `last_destination_searched` 이라는 사용자 지정 속성이 있을 수 있습니다.

{% alert important %}
고객 데이터를 속성으로 가져올 때 사용하는 열 헤더는 기본 사용자 속성의 철자 및 대소문자와 정확히 일치해야 합니다. 그렇지 않으면 Braze가 해당 사용자의 프로필에 사용자 지정 속성을 자동으로 생성합니다.
{% endalert %}

#### 기본 사용자 데이터 열 헤더

| 사용자 프로필 필드 | 데이터 유형 | 정보 | 필수 |
|---|---|---|---|
| `external_id` | 문자열 | 고객에 대한 고유한 사용자 식별자입니다. | 예, [다음 참고 사항](#about-external-ids)을 참조하세요. |
| `user_alias_name` | 문자열 | 익명 사용자를 위한 고유 사용자 식별자입니다. `external_id` 에 대한 대안입니다. | 아니요, [다음 참고 사항](#about-external-ids)을 참조하세요. |
| `user_alias_label` | 문자열 | 사용자 별칭을 그룹화할 수 있는 공통 레이블입니다. | 예, `user_alias_name`을 사용하는 경우. |
| `first_name` | 문자열 | 사용자가 지정한 사용자의 이름(예: `Jane`)입니다. | 아니요 |
| `last_name` | 문자열 | 사용자가 지정한 사용자의 성(예: `Doe`)입니다. | 아니요 |
| `email` | 문자열 | 사용자가 지정한 사용자의 이메일(예: `jane.doe@braze.com`). | 아니요 |
| `country` | 문자열 | 국가 코드는 ISO-3166-1 알파-2 표준(예: `GB`)을 사용하여 Braze에 전달해야 합니다. | 아니요 |
| `dob` | 문자열 | "YYYY-MM-DD" 형식(예: `1980-12-21`)으로 전달해야 합니다. 이렇게 하면 사용자의 생년월일을 가져와서 생일이 "오늘"인 사용자를 타겟팅할 수 있습니다. | 아니요 |
| `gender` | 문자열 | "M", "F", "O"(기타), "N"(해당 없음), "P"(말하지 않음) 또는 nil(알 수 없음)입니다. | 아니요 |
| `home_city` | 문자열 | 사용자가 지정한 사용자의 고향 도시(예: `London`). | 아니요 |
| `language` | 문자열 | ISO-639-1 표준(예: `en`)에 따라 언어를 Braze에 전달해야 합니다. <br>허용되는 언어 목록][1]을 참조하세요. | 아니요 |
| `phone` | 문자열 | 사용자가 지정한 전화번호, `E.164` 형식(예: `+442071838750`)입니다. <br> 서식 지정 지침은 \[사용자 전화번호][2] ]를 참조하세요. | 아니요 |
| `email_open_tracking_disabled` | 부울 | 참 또는 거짓이 허용됩니다.  이 사용자에게 향후 전송되는 모든 이메일에 열린 추적 픽셀이 추가되지 않도록 하려면 true로 설정합니다.   | 아니요 |
| `email_click_tracking_disabled` | 부울 | 참 또는 거짓이 허용됩니다.  이 사용자에게 전송되는 향후 이메일 내의 모든 링크에 대한 클릭 추적을 비활성화하려면 true로 설정합니다. | 아니요 |
| `email_subscribe` | 문자열 | 사용 가능한 값은 `opted_in`(이메일 메시지를 수신하도록 명시적으로 등록됨), `unsubscribed`(이메일 메시지를 수신 거부함), `subscribed`(수신 동의도 거부도 하지 않음)입니다. | 아니요 |
| `push_subscribe` | 문자열 | 사용 가능한 값은 `opted_in`(푸시 메시지 수신을 명시적으로 등록), `unsubscribed`(푸시 메시지 수신을 명시적으로 거부), `subscribed`(수신 동의도 거부도 하지 않음)입니다. | 아니요 |
| `time_zone` | 문자열 | 시간대는 IANA 시간대 데이터베이스와 동일한 형식(예: `America/New_York` 또는 `Eastern Time (US & Canada)`)으로 Braze에 전달해야 합니다.  | 아니요 |
| `date_of_first_session` <br><br> `date_of_last_session`| 문자열 | 다음 ISO-8601 형식 중 하나로 전달할 수 있습니다. {::nomarkdown} <ul> <li> "YYYY-MM-DD" </li> <li> "YYYY-MM-DDTHH:MM:SS+00:00" </li> <li> "YYYY-MM-DDTHH:MM:SSZ" </li> <li> "YYYY-MM-DDTHH:MM:SS"(예: 2019-11-20T18:38:57) </li> </ul> {:/} | 아니요 |
| `subscription_group_id` | 문자열 | 구독 그룹의 `id`. 이 식별자는 대시보드의 구독 그룹 페이지에서 찾을 수 있습니다. | 아니요 |
| `subscription_state` | 문자열 | `subscription_group_id` 에서 지정한 구독 그룹에 대한 구독 상태입니다. 허용되는 값은 `unsubscribed`(구독 그룹에 속하지 않음) 또는 `subscribed`(구독 그룹에 속함)입니다. | 아니요, 하지만 `subscription_group_id` 을 사용하는 경우 강력히 권장합니다. |
{: .reset-td-br-1 .reset-td-br-2 .reset-td-br-3  .reset-td-br-4}

##### 외부 ID 정보

`external_id`는 필수는 아니지만 이 필드 중 하나를 **반드시** 포함해야 합니다. 
- `external_id`: 고객의 고유 사용자 식별자 **또는**
- `braze_id`: 기존 Braze 사용자에 대해 가져온 고유 사용자 식별자 **또는**
- `user_alias_name` 및 `user_alias_label`: 익명 사용자를 위한 고유 사용자 식별자

### 사용자 지정 속성 가져오기

사용자 **가져오기** > **속성**으로 이동하여 사용자에 대한 커스텀 속성을 가져올 수 있습니다. 기본 속성과 정확히 일치하지 않는 헤더는 Braze 내에서 사용자 지정 속성을 생성합니다.

사용자 가져오기에서 허용되는 데이터 유형은 다음과 같습니다:

| 데이터 유형 | 설명 |
|-----------|-------------|
| 날짜 시간 | ISO-8601 형식으로 저장해야 합니다. |
| 부울 | 참 또는 거짓 |
| 숫자 | 공백이나 쉼표가 없는 정수 또는 부동 소수점, 부동 소수점은 마침표(.)를 소수점 구분 기호로 사용해야 합니다. |
| 문자열 | 열 값을 둘러싼 큰따옴표가 있는 한 쉼표를 포함할 수 있습니다 |
| 빈 여백 | 빈 값은 사용자 프로필의 기존 값을 덮어쓰지 않으며, CSV 파일에 기존의 모든 사용자 속성을 포함할 필요는 없습니다. |
{: .reset-td-br-1 .reset-td-br-2}

{% alert important %}
배열 및 푸시 토큰은 사용자 가져오기에서 지원되지 않습니다. 특히 배열의 경우 CSV 파일의 쉼표는 열 구분 기호로 해석되므로 값에 쉼표가 있으면 파일 구문 분석에 오류가 발생합니다. <br>이러한 종류의 값을 업로드하려면 [`/users/track` 엔드포인트]({{site.baseurl}}/api/endpoints/user_data/post_user_track/) 또는 [클라우드 데이터 수집]({{site.baseurl}}/user_guide/data_and_analytics/cloud_ingestion/)을 사용하세요.
{% endalert %}

### 구독 그룹 상태 업데이트하기

사용자 가져오기를 통해 이메일 또는 SMS 구독 그룹에 사용자를 추가할 수 있습니다. 이는 SMS 채널로 메시지를 보내려면 사용자가 SMS 구독 그룹에 등록되어 있어야 하므로 SMS에 특히 유용합니다. 자세한 내용은 [SMS 구독 그룹]({{site.baseurl}}/user_guide/message_building_by_channel/sms/sms_subscription_group/#subscription-group-mms-enablement)을 참조하세요.

정기구독 그룹 상태를 업데이트하는 경우 CSV에 다음 두 열이 있어야 합니다:

- `subscription_group_id`: [구독 그룹]({{site.baseurl}}/user_guide/message_building_by_channel/email/managing_user_subscriptions/#subscription-groups)의 `id`.
- `subscription_state`: 사용 가능한 값은 `unsubscribed`(구독 그룹에 속하지 않음) 또는 `subscribed`(구독 그룹에 속함)입니다.

<style type="text/css">
.tg td{word-break:normal;}
.tg th{word-break:normal;font-size: 14px; font-weight: bold; background-color: #f4f4f7; text-transform: lowercase; color: #212123; font-family: "Sailec W00 Bold",Arial,Helvetica,sans-serif;}
.tg .tg-0pky{border-color:inherit;text-align:left;vertical-align:top;word-break:normal}
</style>
<table class="tg">
<thead>
  <tr>
    <th class="tg-0pky">external_id</th>
    <th class="tg-0pky">first_name</th>
    <th class="tg-0pky">subscription_group_id</th>
    <th class="tg-0pky">subscription_state</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-0pky">A8i3mkd99</td>
    <td class="tg-0pky">Colby</td>
    <td class="tg-0pky">6ff593d7-cf69-448b-aca9-abf7d7b8c273</td>
    <td class="tg-0pky">구독</td>
  </tr>
  <tr>
    <td class="tg-0pky">k2LNhj8Ks</td>
    <td class="tg-0pky">Tom</td>
    <td class="tg-0pky">aea02307-a91e-4bc0-abad-1c0bee817dfa</td>
    <td class="tg-0pky">구독</td>
  </tr>
</tbody>
</table>

{% alert important %}
사용자 가져오기에서 행당 하나의 `subscription_group_id`만 설정할 수 있습니다. 행마다 다른 `subscription_group_id` 값을 가질 수 있습니다. 그러나 동일한 사용자를 여러 구독 그룹에 등록해야 하는 경우에는 여러 번 가져오기를 수행해야 합니다.
{% endalert %}

### 사용자 지정 이벤트 가져오기(미리 보기) {#importing-custom-events}

{% alert important %}
커스텀 이벤트 가져오기는 현재 얼리 액세스 중입니다. 얼리 액세스에 참여하려면 Braze 계정 매니저에게 문의하세요.
{% endalert %}

사용자에 대한 커스텀 이벤트를 가져오려면 사용자 **가져오기** > **이벤트**로 이동합니다.

사용자 지정 이벤트는 비즈니스에 맞게 맞춤 설정할 수 있습니다. 예를 들어 스트리밍 앱에는 rented_movie라는 커스텀 이벤트가 있을 수 있습니다. CSV에 열 머리글이 있어야 합니다:

- 다음 중 하나를 선택합니다:
  - `external_id`**또는**
  - `braze_id`**또는** 
  - `user_alias_name` 및 `user_alias_label`
- 이름
- 시간

사용자 지정 이벤트에는 이벤트 속성이 있을 수 있습니다. 예를 들어, 커스텀 이벤트인 rented_movie에는 속성 제목과 장르가 있을 수 있습니다. 이러한 이벤트 속성의 열 헤더는 `<event_name>.properties.<property name>` 여야 합니다. 예는 `rented_movie.properties.title` 입니다.

| 사용자 프로필 필드                      | 데이터 유형 | 정보                                                                                                                                                                                                             | 필수                                                                                        |
|-----------------------------------------|-----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------|
| `external_id`                           | 문자열    | 사용자의 고유한 사용자 식별자입니다.                                                                                                                                                                                 | 예, `external_id`, `braze_id`, 또는 `user_alias_name` 및 `user_alias_label` 중 하나가 필요합니다. |
| `braze_id`                              | 문자열    | 사용자에 대해 Braze에서 할당된 식별자입니다.                                                                                                                                                                              | 예, `external_id`, `braze_id`, 또는 `user_alias_name` 및 `user_alias_label` 중 하나가 필요합니다. |
| `user_alias_name`                       | 문자열    | 익명 사용자를 위한 고유 사용자 식별자입니다. external_id의 대체 항목입니다.                                                                                                                                        | 예, `external_id`, `braze_id`, 또는 `user_alias_name` 및 `user_alias_label` 중 하나가 필요합니다. |
| `user_alias_label`                      | 문자열    | 사용자 별칭을 그룹화할 수 있는 공통 레이블입니다.                                                                                                                                                                          | 예, `external_id`, `braze_id`, 또는 `user_alias_name` 및 `user_alias_label` 중 하나가 필요합니다. |
| `name`                                  | 문자열    | 사용자의 사용자 지정 이벤트.                                                                                                                                                                                           | 예                                                                                             |
| `time`                                  | 문자열    | 이벤트 시간입니다. 다음 ISO-8601 형식 중 하나로 전달할 수 있습니다. {::nomarkdown} <ul> <li> "YYYY-MM-DD" </li> <li> "YYYY-MM-DDTHH:MM:SS+00:00" </li> <li> "YYYY-MM-DDTHH:MM:SSZ" </li> <li> "YYYY-MM-DDTHH:MM:SS"(예: 2019-11-20T18:38:57) </li> </ul> {:/} | 예                                                                                             |
| `<event name>.properties.<property name>` | 다중  | 사용자 지정 이벤트와 연결된 이벤트 속성입니다. 예는`rented_movie.properties.title`입니다.                                                                                                                        | 아니요                                                                                              |
{: .reset-td-br-1 .reset-td-br-2 .reset-td-br-3  .reset-td-br-4}

{% alert note %}
external_id 자체는 필수는 아니지만 다음 필드 중 하나를 반드시 포함해야 합니다: <br>- `external_id`: 고객에 대한 고유 사용자 식별자 <br>- `braze_id`: 기존 Braze 사용자를 위해 가져온 고유 사용자 식별자 <br>- `user_alias_name`: 익명 사용자를 위한 고유 사용자 식별자
{% endalert %}

#### CSV 크기

Braze는 최대 500MB 크기의 파일에서 표준 CSV 형식의 사용자 데이터를 허용합니다. CSV 파일 템플릿 중 하나를 다운로드하려면 [외부 ID로 가져오기](#importing-with-external-id) 또는 [사용자 별칭으로 가져오기](#importing-with-user-alias)를 참조하세요.

#### 데이터 포인트 고려 사항

CSV를 통해 가져온 각 고객 데이터는 고객 프로필의 기존 값을 덮어쓰며 외부 ID와 빈 값을 제외하고 데이터 포인트로 계산됩니다.

- CSV 가져오기를 통해 업로드된 외부 ID는 데이터 포인트를 소비하지 않습니다. 외부 ID만 업로드하여 기존 Braze 사용자를 세분화하기 위해 CSV 파일을 업로드하는 경우, 데이터 포인트를 소비하지 않고도 이 작업을 수행할 수 있습니다. 가져오기에서 사용자의 이메일이나 전화번호와 같은 추가 데이터를 추가하면 기존 사용자 데이터를 덮어쓰고 데이터 포인트를 소모하게 됩니다.
    - 세분화 목적의 CSV 가져오기(`external_id`, `braze_id`, 또는 `user_alias_name`을 유일한 필드로 사용하여 가져오기)는 데이터 포인트를 소비하지 않습니다.
- 빈 값은 고객 프로필의 기존 값을 덮어쓰지 않으며, 기존의 모든 사용자 속성이나 커스텀 이벤트를 CSV 파일에 포함할 필요는 없습니다.
- `email_subscribe`, `push_subscribe`, `subscription_group_id` 또는 `subscription_state`를 업데이트하는 것은 데이터 포인트 소비에 포함되지 않습니다.

{% alert important %}
CSV 가져오기 또는 API를 통해 사용자에 대한 언어 또는 국가를 설정하면 Braze가 SDK를 통해 이 정보를 자동으로 캡처하지 못합니다.
{% endalert %}

## CSV 가져오기

CSV 파일을 가져오려면
1. **오디언스** > **사용자 가져오기**로 이동합니다. 
2. **파일 찾아보기**를 선택하고 관심 있는 파일을 선택한 다음 **가져오기 시작**을 선택합니다. Braze는 파일을 업로드하고 열 헤더와 각 열의 데이터 유형을 확인합니다.

{% alert important %}
CSV 가져오기는 대소문자를 구분합니다. 즉, CSV 가져오기에서 대문자는 표준 속성이 아닌 커스텀 속성으로 필드를 작성합니다. 예를 들어 "이메일"이 맞지만 "이메일"은 커스텀 속성으로 작성됩니다.
{% endalert %}

![가져올 사용자 정보 유형으로 '이벤트' 옵션이 선택되어 있습니다.][5]

업로드가 완료되면 파일 콘텐츠의 미리 보기를 볼 수 있습니다. 테이블의 정보는 CSV 파일의 맨 위 행에 있는 값을 기반으로 합니다.

5초마다 새로 고쳐지는 **사용자 가져오기** 페이지에서 또는 **테이블 새로 고침을** 선택하면 진행 상황을 추적할 수 있습니다. 가져오기 중에도 나머지 Braze 대시보드는 계속 사용할 수 있으며, 가져오기가 시작되고 종료되면 알림을 받게 됩니다.

또한 가장 최근에 가져온 파일, 파일 이름, CSV 유형, 파일의 줄 수, 성공적으로 가져온 줄 수, 각 파일의 총 줄 수 및 각 가져오기 상태를 볼 수 있습니다.

동시에 두 개 이상의 CSV 파일을 가져올 수 있습니다. CSV 가져오기는 동시에 실행되므로 업데이트 순서가 순차적으로 보장되지 않습니다. CSV 가져오기를 차례로 실행해야 하는 경우, CSV 가져오기가 완료될 때까지 기다렸다가 두 번째 가져오기를 업로드해야 합니다.

가져오기 프로세스에서 오류가 발생하면 파일의 총 줄 수 옆에 경고 아이콘이 표시됩니다. 아이콘 위로 마우스를 가져가면 특정 회선이 실패한 이유에 대한 자세한 내용을 확인할 수 있습니다. 가져오기가 완료되면 모든 데이터가 기존 프로필에 추가되거나 새 프로필이 만들어집니다.

![단일 열에 데이터 유형이 혼합된 오류로 CSV 파일 업로드가 완료되었습니다][4]{: style="max-width:70%"}

### 고려 사항

업로드 중 Braze가 파일의 맨 위 행에서 잘못된 내용을 발견하면 이러한 오류는 요약과 함께 표시됩니다. 예를 들어 파일에 잘못된 행이 포함된 경우 파일을 가져올 때 미리보기에 이 오류가 표시됩니다. 오류가 있는 파일을 가져올 수 있지만 가져오기를 계속하기 전에 파일에서 이러한 오류를 수정하는 것이 좋습니다.

또한 Braze는 미리보기를 위해 입력 파일의 모든 행을 스캔하지 않으므로 업로드하기 전에 전체 CSV 파일을 검토하는 것이 중요합니다. 즉, 이 미리보기를 생성하는 동안 Braze가 포착하지 못한 오류가 존재할 수 있습니다.

잘못된 행과 외부 ID가 없는 행은 가져오지 않습니다. 다른 모든 오류는 가져올 수 있지만 세그먼트 생성 시 필터링에 방해가 될 수 있습니다. 자세한 내용은 [문제 해결](#troubleshooting) 섹션으로 건너뛰세요.

{% alert warning %}
오류는 전적으로 데이터 유형과 파일 구조에 따라 발생합니다. 예를 들어 형식이 잘못된 이메일 주소도 여전히 문자열로 구문 분석할 수 있으므로 가져올 수 있습니다.
{% endalert %}

### 람다 사용자 CSV 가져오기

서버리스 S3 Lambda CSV 가져오기 스크립트를 사용하여 사용자 속성을 플랫폼에 업로드할 수 있습니다. 이 솔루션은 CSV 업로더로 작동하며, CSV를 S3 버킷에 넣으면 스크립트가 API를 통해 업로드합니다.

100만 행이 있는 파일의 예상 실행 시간은 5분 정도입니다. 자세한 내용은 [사용자 속성 CSV를 Braze로 가져오기]({{site.baseurl}}/user_csv_lambda/)를 참조하세요.

## 세분화

사용자 가져오기는 사용자 프로필을 만들고 업데이트하며 세그먼트를 만드는 데에도 사용할 수 있습니다. 세그먼트를 만들려면 가져오기를 시작하기 전에 **이 CSV에서 가져온 사용자로부터 세그먼트 자동 생성**을 선택합니다.

세그먼트의 이름을 설정하거나 파일 이름인 기본값을 그대로 사용할 수 있습니다. 세그먼트를 만드는 데 사용된 파일에는 가져오기가 완료된 후 세그먼트를 볼 수 있는 링크가 표시됩니다.

세그먼트를 만드는 데 사용되는 필터는 선택한 가져오기에서 생성되거나 업데이트된 사용자를 선택하며 세그먼트 편집 페이지의 다른 모든 필터와 함께 사용할 수 있습니다.

## 문제 해결 {#troubleshooting}

### 누락된 행

가져온 사용자 수가 CSV 파일의 총 행 수와 일치하지 않는 데에는 몇 가지 이유가 있습니다.

- **중복된 외부 ID:** 외부 ID 열이 중복된 경우 행의 형식이 올바르게 지정되어 있어도 잘못된 형식이거나 가져오지 않은 행이 발생할 수 있습니다. 경우에 따라 특정 오류를 보고하지 않을 수도 있습니다. CSV에 중복된 외부 ID가 있는지 확인합니다. 그렇다면 중복 항목을 제거하고 다시 업로드해 보세요.
- **악센트 문자:** CSV 파일에 악센트가 포함된 이름이나 속성이 있을 수 있습니다. 문제를 방지하려면 파일을 항상 UTF-8로 인코딩하세요.

### 잘못된 행

데이터를 올바르게 가져오려면 CSV 파일에 헤더 행을 포함해야 합니다. 각 행에는 머리글 행과 동일한 수의 셀이 있어야 합니다. 길이가 헤더 행보다 크거나 작은 값의 행은 가져오기에서 제외됩니다. 값의 쉼표는 구분 기호로 해석되어 이 오류가 발생할 수 있습니다. 또한 모든 데이터는 UTF-8로 인코딩되어야 합니다.

CSV 파일에 빈 행이 있고 가져오는 행 수가 CSV 파일의 전체 행 수보다 적은 경우 빈 행은 가져올 필요가 없으므로 가져오기에 문제가 없는 것으로 간주할 수 있습니다. 올바르게 가져온 회선 수를 확인하고 가져오려는 사용자 수와 일치하는지 확인하세요.

### 여러 데이터 유형

Braze는 열의 각 값이 동일한 데이터 유형일 것으로 예상합니다. 속성의 데이터 유형과 일치하지 않는 값은 세그먼테이션에 오류를 일으킵니다.

### 잘못된 형식의 날짜

[ISO-8601](https://en.wikipedia.org/wiki/ISO_8601) 형식이 아닌 날짜는 가져오기 시 날짜 시간으로 읽히지 않습니다.

### 문자열 따옴표

작은따옴표('') 또는 큰따옴표("")로 묶인 값은 가져오기 시 문자열로 읽힙니다.

### 사용자 지정 속성으로 가져온 데이터

사용자 지정 속성으로 가져온 기본 사용자 데이터(예: `email` 또는 `first_name`)가 표시되는 경우 CSV 파일의 대소문자와 띄어쓰기를 확인하세요. 예를 들어 `First_name`은 커스텀 속성으로 가져오지만 `first_name`은 고객 프로필의 '이름' 필드에 올바르게 가져옵니다.

\[import_template]: {% image_buster /assets/download_file/braze-user-import-template-csv.xlsx %}
\[events_template]: {% image_buster /assets/download_file/braze-csv-events-import-template.csv %}
\[template_alias_attributes]: {% image_buster /assets/download_file/braze-user-import-alias-template-csv.xlsx %}
\[template_alias_events]: {% image_buster /assets/download_file/braze-events-csv-example-user-alias.csv %}
\[오류]:#common-errors
[1]: {{site.baseurl}}/user_guide/data_and_analytics/user_data_collection/language_codes/
[2]: {{site.baseurl}}/user_guide/message_building_by_channel/sms/phone_numbers/user_phone_numbers/
[12]: {{site.baseurl}}/api/endpoints/user_data/post_user_track/
[13]: {{site.baseurl}}/user_guide/data_and_analytics/user_data_collection/user_profile_lifecycle/
[14]: {{site.baseurl}}/user_guide/data_and_analytics/cloud_ingestion/
[3]: {% image_buster /assets/img/importcsv5.png %}
[4]: {% image_buster /assets/img/importcsv2.png %}
[5]: {% image_buster /assets/img/importcsv3.png %}
[7]: {% image_buster /assets/img/segment-imported-users.png %}
[8]: {% image_buster /assets/img_archive/user_alias_import_1.png %}
[9]: {% image_buster /assets/img/subscription_group_import.png %}