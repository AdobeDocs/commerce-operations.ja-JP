---
title: キャッシュポイズニングの防止
description: Commerce ストアフロントのページキャッシュポイズニングを防止する方法について説明します。
feature: Configuration, Cache, Security
exl-id: 947024dd-d59d-480d-bb6c-8e0065054bb6
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
    internal-label: Security
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
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
source-wordcount: '265'
ht-degree: 0%
---
# キャッシュポイズニングの防止

このトピックでは、Microsoft Internet Information Server （IIS） Web サーバーを使用する場合にキャッシュ ポイズニングを防止する方法について説明します。 _キャッシュ ポイズニング_&#x200B;は、キャッシュの内容を変更して、同じサイトの異なるページを含める方法です。 例えば、一部の正常なページ（ストアフロントホームページなど）の代わりにHTTP 404 （Not Found）エラーページを挿入すると、サービス拒否（DoS）が発生する可能性があります。 悪意のあるページ URLはVarnishまたはRedisによってキャッシュされるため、名前は&#x200B;_page cache poisoning_&#x200B;です。

これらのタイプの攻撃は、web サーバーのログにエラーが発生しないため、検出が困難になる可能性があります。

このソリューションは、次のCommerce バージョンに適用されます。

- 2.0.10以降
- 2.1.2以降

>[!INFO]
>
>このトピックは、経験豊富なIIS管理者向けです。

## 説明

この問題は、URLの書き換えがIIS サーバーで有効になっていて、要求がVarnishまたはRedis キャッシングサービスに到達する前に、次のHTTP ヘッダーのいずれかが変更された場合に発生します。

- `X-Rewrite-Url`
- `X-Original-Url`
- `IIS-wasurlrewritten`
- `Unencoded-URL`
- `Orig-path-info`

これらのヘッダーが変更されると、結果のURLとコンテンツがキャッシュされ、潜在的な脆弱性が発生します。

## Solution

`Enable_IIS_Rewrites`のIIS サーバー設定に基づいて、前述のすべてのヘッダーの値を削除するオプションを提供します。

- `Enable_IIS_Rewrites`が`0`に設定されている場合、ヘッダーの値は削除されます。
- `Enable_IIS_Rewrites`が`1`に設定されている場合、ヘッダーの値はそのまま残ります。

>[!WARNING]
>
>`Enable_IIS_Rewrites`を`1`に設定した場合、要求がIIS Web サーバーに到達する前に、前のヘッダーの値を変更しないでください。
