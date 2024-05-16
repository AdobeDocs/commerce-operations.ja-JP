---
title: この [!UICONTROL Security] タブ
description: について説明します [!UICONTROL Security] タブ / [!DNL Observation for Adobe Commerce].
exl-id: b567e4a4-534e-4151-b6f6-bf59b1bd4028
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# この [!UICONTROL Security] タブ

この **[!UICONTROL Security]** tab キーは、セキュリティ上の問題を説明し、その潜在的な原因を分離します。 さらに、タブのフレームを記述する。

## [!UICONTROL API calls by IP, details by URL]

この **[!UICONTROL API calls by IP, details by URL]** フレームは、選択した期間における IP による API 呼び出しの数を表示します。 このフレームには、IP アドレスと、その IP アドレスによってアクセスされた API URL が表示されます。

![IP による API 呼び出し](../../assets/tools/observation-for-adobe-commerce/calls-by-ip.jpg)

## [!UICONTROL Forgot Password]

この **[!UICONTROL Forgot Password]** アクセスフレームには、選択した期間におけるパスワードを忘れた場合の試行回数が表示されます。 IP アドレスに対するアクティビティが高いと、サイトが攻撃される可能性があります。

![パスワードを忘れる](../../assets/tools/observation-for-adobe-commerce/forgot-password.jpg)

## [!UICONTROL Create Account access]

この **[!UICONTROL Create Account access]** フレーム：選択した期間における新しいアカウントアクティビティの数を表示します。 単一の IP アドレスからのアクティビティが多い場合は、攻撃が行われている可能性があります。

![create-account-access](../../assets/tools/observation-for-adobe-commerce/create-account-access.png)

## [!UICONTROL POST activities]

この **[!UICONTROL POST activities]** フレームは、 `POST` サイトのアクティビティ （ファセット日） `client_ip` から [!DNL Fastly] ログ。 また、IP アドレスによってアクセスされる URL も表示されます。

![POSTアクティビティ](../../assets/tools/observation-for-adobe-commerce/POST-activities.jpg)

## [!UICONTROL POST activities summary table]

この **[!UICONTROL POST activities summary table]** フレームは要約された `POST` サイトのアクティビティ （ファセット日） `client_ip` から [!DNL Fastly] ログ。 また、IP アドレスによってアクセスされる URL の数も表示されます。 選択した期間のカウントが表示されます。

![POSTアクティビティの概要](../../assets/tools/observation-for-adobe-commerce/POST-activities-summary.jpg)

## [!UICONTROL POST activities details table]

この **[!UICONTROL POST activities details table]** フレームは、 `POST` からのサイトのアクティビティ [!DNL Fastly] ログ。 また、からの詳細もすべて表示されます [!DNL Fastly] これらのリクエストのログ。 過去 2000 件のリクエストに制限されています。
![POSTアクティビティの詳細](../../assets/tools/observation-for-adobe-commerce/POST-activities-details.jpg)

## [!UICONTROL Guest Carts activities]

この **[!UICONTROL Guest Carts activities]** フレームは、選択した期間におけるゲストの買い物かごアクティビティ数を、IP アドレスとアクセスした URL を使用してファセット表示します。 ゲストの買い物かごは、カード攻撃で使用される場合があります。 このフレームには、ゲストカートの URL にアクセスしたリクエストの合計数が表示されます。

![guest-carts-activities](../../assets/tools/observation-for-adobe-commerce/guest-carts-activities.jpg)

## [!UICONTROL API – forgot password, create account by Countries]

この **[!UICONTROL API – forgot password, create account by Countries]** フレームには、作成されたアカウントの数と、選択した期間で忘れたパスワードをリセットするためのリクエストが表示されます。 リクエストの原産国も示すようにファセットされています。 このフレームは、リクエストの原産国に焦点を当てています。

![api-forgot-countries](../../assets/tools/observation-for-adobe-commerce/api-forgot-countries.jpg)

## [!UICONTROL API - forgot password, create account by Countries and IP address]

この **[!UICONTROL API - forgot password, create account by Countries and IP address]** フレームには、作成されたアカウントの数と、選択した期間で忘れたパスワードをリセットするためのリクエストが表示されます。 リクエストの IP アドレス、アクセスした URL、および起源の国も表示するようにファセットされています。 このフレームは、IP の数に焦点を当てています。

![api-forgot-countries-ip](../../assets/tools/observation-for-adobe-commerce/api-forgot-countries-ip.png)

## [!UICONTROL Guest cart activities by IP]

この **[!UICONTROL Guest cart activities by IP]** フレームは、選択した期間、IP 別のゲストの買い物かごアクティビティを表示します。

![guest-cart-ip](../../assets/tools/observation-for-adobe-commerce/guest-cart-ip.png)

## [!UICONTROL Guest cart activities by Countries]

この **[!UICONTROL Guest cart activities by Countries]** フレーム：選択した期間における国別のゲストの買い物かごアクティビティを表示します。

![guest-cart-country](../../assets/tools/observation-for-adobe-commerce/guest-cart-country.png)
