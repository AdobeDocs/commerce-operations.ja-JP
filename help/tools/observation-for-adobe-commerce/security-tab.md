---
title: 「 [!UICONTROL Security] タブ"
description: 詳しくは、 [!UICONTROL Security] タブ [!DNL Observation for Adobe Commerce].
source-git-commit: 297c3fed4c0f7ad1a3cb40addef1d33fa8d41525
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---


# この [!UICONTROL Security] タブ

この **[!UICONTROL Security]** 「 」タブでは、セキュリティ上の問題について説明し、潜在的な原因を特定します。 また、タブのフレームについて述べた。

## [!UICONTROL API calls by IP, details by URL]

この **[!UICONTROL API calls by IP, details by URL]** frame は、選択した期間にわたる IP による API 呼び出しの数を表示します。 このフレームには、IP アドレスと、その IP アドレスからアクセスされた API URL が表示されます。

![IP による API 呼び出し](../../assets/tools/observation-for-adobe-commerce/calls-by-ip.jpg)

## [!UICONTROL Forgot Password]

この **[!UICONTROL Forgot Password]** アクセスフレームには、選択した期間にパスワードを忘れた場合の試行回数が表示されます。 IP アドレスに対する高いアクティビティは、サイトへの攻撃である可能性があります。

![パスワードを忘れた場合](../../assets/tools/observation-for-adobe-commerce/forgot-password.jpg)

## [!UICONTROL Create Account access]

この **[!UICONTROL Create Account access]** frame は、選択した期間の新しいアカウントアクティビティの数を表示します。 単一の IP アドレスからの高いアクティビティは、攻撃を示す可能性があります。

![create-account-access](../../assets/tools/observation-for-adobe-commerce/create-account-access.png)

## [!UICONTROL POST activities]

この **[!UICONTROL POST activities]** frame は、 `POST` サイトの活動、ファセット `client_ip` から [!DNL Fastly] ログ。 また、IP アドレスからアクセスされる URL も表示されます。

![POST — アクティビティ](../../assets/tools/observation-for-adobe-commerce/POST-activities.jpg)

## [!UICONTROL POST activities summary table]

この **[!UICONTROL POST activities summary table]** フレームに要約された内容が表示されます `POST` サイトの活動、ファセット `client_ip` から [!DNL Fastly] ログ。 また、IP アドレスからアクセスされる URL の数も表示されます。 カウントは、選択した期間のものです。

![POST — アクティビティ — 概要](../../assets/tools/observation-for-adobe-commerce/POST-activities-summary.jpg)

## [!UICONTROL POST activities details table]

この **[!UICONTROL POST activities details table]** frame は、 `POST` サイトのアクティビティ [!DNL Fastly] ログ。 また、 [!DNL Fastly] ログに記録して、これらのリクエストを確認します。 最後の 2000 件のリクエストに制限されます。
![POST — アクティビティ — 詳細](../../assets/tools/observation-for-adobe-commerce/POST-activities-details.jpg)

## [!UICONTROL Guest Carts activities]

この **[!UICONTROL Guest Carts activities]** frame は、選択した期間内のゲストカートアクティビティの数を、IP アドレスとアクセスされた URL でファセット化して表示します。 客車はカーディング攻撃に使用される場合がある。 このフレームは、ゲストカートの URL にアクセスした要求の合計数を示します。

![guest-carts-activities](../../assets/tools/observation-for-adobe-commerce/guest-carts-activities.jpg)

## [!UICONTROL API – forgot password, create account by Countries]

この **[!UICONTROL API – forgot password, create account by Countries]** frame は、作成されたアカウントの数と、選択した期間に忘れたパスワードをリセットするためのリクエストの数を表示します。 依頼の起源を示す面もある。 このフレームは、リクエストの原産国に焦点を当てます。

![api-forgot-countries](../../assets/tools/observation-for-adobe-commerce/api-forgot-countries.jpg)

## [!UICONTROL API - forgot password, create account by Countries and IP address]

この **[!UICONTROL API - forgot password, create account by Countries and IP address]** frame は、作成されたアカウントの数と、選択した期間に忘れたパスワードをリセットするためのリクエストの数を表示します。 リクエストの IP アドレス、アクセスされた URL、接触チャネル（接触チャネル）も表示できます。 このフレームは、IP の数に焦点を当てています。

![api-forgot-countries-ip](../../assets/tools/observation-for-adobe-commerce/api-forgot-countries-ip.png)

## [!UICONTROL Guest cart activities by IP]

この **[!UICONTROL Guest cart activities by IP]** frame は、選択した期間でのゲストカートのアクティビティを IP 別に表示します。

![guest-cart-ip](../../assets/tools/observation-for-adobe-commerce/guest-cart-ip.png)

## [!UICONTROL Guest cart activities by Countries]

この **[!UICONTROL Guest cart activities by Countries]** frame は、選択した期間の国別のゲストカートアクティビティを表示します。

![guest-cart-country](../../assets/tools/observation-for-adobe-commerce/guest-cart-country.png)
