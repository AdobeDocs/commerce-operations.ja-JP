---
title: 「[!DNL WAF]」タブ
description: '[!DNL Observation for Adobe Commerce]の「[!DNL WAF]」タブについて説明します。'
exl-id: e36986d7-d903-4154-bb09-6962b99ae35f
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
source-wordcount: '168'
ht-degree: 0%
---
# 「[!DNL WAF]」タブ

「**[!DNL WAF]**」タブには、[!DNL firewall]によって渡され、ブロックされたトラフィックが表示されます。

## [!DNL WAF traffic summary]

![WAF トラフィックの概要](../../assets/tools/observation-for-adobe-commerce/waf-1.png)

**[!DNL WAF traffic summary]** フレームは、[!DNL firewall]によって渡され、ログに記録され、ブロックされ、失敗したトラフィックの数を示します。

## [!DNL WAF Top 10 blocked IP Addresses]

![WAFのブロックされたIP アドレスの上位10件](../../assets/tools/observation-for-adobe-commerce/waf-2.png)

**[!DNL WAF Top 10 blocked IP Addresses]** フレームには、[!DNL firewall]によって最もブロックされた上位10個のIP アドレスが表示されます。

## [!DNL WAF Top 10 countries for blocked requests]

![ ブロックされたリクエストのWAF上位10か国](../../assets/tools/observation-for-adobe-commerce/waf-3.jpg)

**[!DNL WAF Top 10 countries for blocked requests]** フレームには、[!DNL firewall]によるブロック済みリクエストの上位10以内の国に対するブロック済みリクエストの数が表示されます。

## [!DNL WAF Top 10 logged IP Addresses]

![WAFのログに記録された上位10個のIP アドレス ](../../assets/tools/observation-for-adobe-commerce/waf-4.jpg)

**[!DNL WAF Top 10 logged IP Addresses]** フレームには、[!DNL firewall]によって記録された上位10個のIP アドレスにIP アドレスが表示されます。

## [!DNL Top 10 WAF Rules Executed and Logged by IP address]

![IP アドレスによって実行および記録された上位10個のWAF ルール ](../../assets/tools/observation-for-adobe-commerce/waf-5.jpg)

**[!DNL Top 10 WAF Rules Executed and Logged by IP address]** フレームには、上位10件のIP アドレスが表示されます。最も頻繁に一致するのは[!DNL firewall] ルールです。

## [!DNL WAF Logged Details]

![WAFがログに記録した詳細](../../assets/tools/observation-for-adobe-commerce/waf-6.jpg)

**[!DNL WAF Logged Details]** フレームには、[!DNL firewall]によって記録されたリクエストが表示され、タイムスタンプ、市区町村、地域、データセンターなどの詳細が表示されます。

## [!DNL WAF Blocked Details]

![WAF ブロックの詳細](../../assets/tools/observation-for-adobe-commerce/waf-7.jpg)

**[!DNL WAF Blocked Details]** フレームには、[!DNL firewall]によってブロックされたリクエスト（タイムスタンプ、市区町村、地域、データセンターなど）が表示されます。
