---
title: キャッシュのポイズニングを防止
description: Commerce ストアフロントでページキャッシュの不正使用を防ぐ方法を説明します。
feature: Configuration, Cache, Security
exl-id: 947024dd-d59d-480d-bb6c-8e0065054bb6
source-git-commit: 56a2461edea2799a9d569bd486f995b0fe5b5947
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---

# キャッシュのポイズニングを防止

ここでは、Microsoft Internet Information Server （IIS） Web サーバを使用する場合に、キャッシュ ポイズニングを防止する方法について説明します。 _キャッシュの被毒_ は、キャッシュコンテンツを変更して、同じサイトの異なるページを含める方法です。 例えば、無害なページ（ストアフロントのホームページなど）の代わりに HTTP 404 （見つかりません）エラーページを挿入し、サービス拒否（DoS）の可能性につながる可能性があります。 悪意のあるページの URL は、Varnish または Redis によってキャッシュされるので、という名前が付けられます _ページキャッシュの使用_.

これらのタイプの攻撃は、web サーバーのログにエラーが記録されないので、検出が困難な場合があります。

このソリューションは、次のCommerce バージョンに適用されます。

- 2.0.10 以降
- 2.1.2 以降

>[!INFO]
>
>このトピックは、経験豊富な IIS 管理者を対象としています。

## 説明

この問題は、URL の書き換えが IIS サーバーで有効になっており、リクエストが Varnish または Redis キャッシュサービスに到達する前に、次の HTTP ヘッダーのいずれかが変更された場合に発生します。

- `X-Rewrite-Url`
- `X-Original-Url`
- `IIS-wasurlrewritten`
- `Unencoded-URL`
- `Orig-path-info`

これらのヘッダーが変更されると、結果として生成される URL とコンテンツがキャッシュされるので、潜在的な脆弱性が発生します。

## 解決策

IIS サーバーの設定に基づいて、上記のすべてのヘッダーの値を削除するオプションを提供します。 `Enable_IIS_Rewrites`.

- 次の場合 `Enable_IIS_Rewrites` はに設定されています。 `0`の場合、ヘッダーの値は削除されます。
- 次の場合 `Enable_IIS_Rewrites` はに設定されています。 `1`の場合、ヘッダーの値は変更されません。

>[!WARNING]
>
>を設定した場合 `Enable_IIS_Rewrites` 対象： `1`は、要求が IIS Web サーバーに到達する前に、前のヘッダーの値を変更できないようにする必要があります。
