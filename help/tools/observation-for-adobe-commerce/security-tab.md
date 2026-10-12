---
title: 「[!UICONTROL Security]」タブ
description: '[!DNL Observation for Adobe Commerce]の「[!UICONTROL Security]」タブについて説明します。'
exl-id: b567e4a4-534e-4151-b6f6-bf59b1bd4028
feature: Configuration, Observability
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: 4239b8a6-e74f-567d-a7a5-b98b9ead0ea4
    internal-label: Observability
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%
---
# 「[!UICONTROL Security]」タブ

「**[!UICONTROL Security]**」タブでは、セキュリティの問題について説明し、その潜在的な原因を特定します。 さらに、タブのフレームについて説明する。

## [!UICONTROL API calls by IP, details by URL]

**[!UICONTROL API calls by IP, details by URL]** フレームには、選択した期間におけるIPによるAPI呼び出しの数が表示されます。 このフレームには、IP アドレスと、そのIP アドレスによってアクセスされたAPI URLが表示されます。

IP](../../assets/tools/observation-for-adobe-commerce/calls-by-ip.jpg)による![API呼び出し

## [!UICONTROL Forgot Password]

**[!UICONTROL Forgot Password]** アクセス フレームには、選択した期間にパスワードを忘れた回数が表示されます。 IP アドレスに対する高いアクティビティは、サイト上の攻撃である可能性があります。

![ パスワードを忘れた](../../assets/tools/observation-for-adobe-commerce/forgot-password.jpg)

## [!UICONTROL Create Account access]

**[!UICONTROL Create Account access]** フレームには、選択した期間における新しいアカウントアクティビティの数が表示されます。 単一のIP アドレスからのアクティビティが多い場合は、攻撃を示している可能性があります。

![create-account-access](../../assets/tools/observation-for-adobe-commerce/create-account-access.png)

## [!UICONTROL POST activities]

**[!UICONTROL POST activities]** フレームには、[!DNL Fastly]件のログから`client_ip`にファセットされた、サイトの`POST`件のアクティビティが表示されます。 また、IP アドレスからアクセスされるURLも表示されます。

![ アクティビティ後](../../assets/tools/observation-for-adobe-commerce/POST-activities.jpg)

## [!UICONTROL POST activities summary table]

**[!UICONTROL POST activities summary table]** フレームには、[!DNL Fastly]件のログから`client_ip`にファセットされた、サイトの要約`POST`件のアクティビティが表示されます。 また、IP アドレスによってアクセスされるURLの数も表示されます。 カウントは選択した期間のものです。

![ アクティビティ後の概要](../../assets/tools/observation-for-adobe-commerce/POST-activities-summary.jpg)

## [!UICONTROL POST activities details table]

**[!UICONTROL POST activities details table]** フレームには、[!DNL Fastly] ログからのサイトの`POST` アクティビティが表示されます。 また、これらのリクエストの[!DNL Fastly] ログのすべての詳細も表示されます。 最後の2000件のリクエストに限定されます。
![POST-activities-details](../../assets/tools/observation-for-adobe-commerce/POST-activities-details.jpg)

## [!UICONTROL Guest Carts activities]

**[!UICONTROL Guest Carts activities]** フレームには、選択した期間におけるゲスト カート アクティビティの数が、IP アドレスとアクセスされたURLによってファセットされて表示されます。 ゲストカートはカード攻撃に使用される可能性があります。 このフレームは、ゲストカートのURLにアクセスしたリクエストの合計数を示します。

![guest-carts-activities](../../assets/tools/observation-for-adobe-commerce/guest-carts-activities.jpg)

## [!UICONTROL API – forgot password, create account by Countries]

**[!UICONTROL API – forgot password, create account by Countries]** フレームには、選択した期間にパスワードを忘れた場合にリセットするアカウントの作成数とリクエスト数が表示されます。 リクエストの原産国も表示されます。 このフレームは、リクエストの原産国に焦点を当てています。

![api-forgot-countries](../../assets/tools/observation-for-adobe-commerce/api-forgot-countries.jpg)

## [!UICONTROL API - forgot password, create account by Countries and IP address]

**[!UICONTROL API - forgot password, create account by Countries and IP address]** フレームには、選択した期間にパスワードを忘れた場合にリセットするアカウントの作成数とリクエスト数が表示されます。 ファセットには、リクエストのIP アドレス、アクセスされたURL、および送信元の国も表示されます。 このフレームはIPのカウントに焦点を当てています。

![api-forgot-countries-ip](../../assets/tools/observation-for-adobe-commerce/api-forgot-countries-ip.png)

## [!UICONTROL Guest cart activities by IP]

**[!UICONTROL Guest cart activities by IP]** フレームには、選択した期間のIP別のゲスト カート アクティビティが表示されます。

![guest-cart-ip](../../assets/tools/observation-for-adobe-commerce/guest-cart-ip.png)

## [!UICONTROL Guest cart activities by Countries]

**[!UICONTROL Guest cart activities by Countries]**&#x200B;枠には、選択した期間の国ごとのゲストカート活動が表示されます。

![guest-cart-country](../../assets/tools/observation-for-adobe-commerce/guest-cart-country.png)
