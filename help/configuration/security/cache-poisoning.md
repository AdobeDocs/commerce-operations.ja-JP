---
title: キャッシュポイズニングを防ぐ
description: コマースストアフロントでページキャッシュ中毒を防ぐ方法を説明します。
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 0%

---


# キャッシュポイズニングを防ぐ

このトピックでは、を防ぐ方法について説明します [キャッシュ](https://glossary.magento.com/cache) Microsoft Internet Information Server(IIS)Web サーバーを使用している場合に中毒 _キャッシュ中毒_ は、同じサイトの異なるページを含むようにキャッシュコンテンツを変更する方法です。 例えば、問題のないページ ( 例えば、 [店頭](https://glossary.magento.com/storefront) ホームページ ) で始まり、DoS(DoS) が発生する可能性があります。 悪意のあるページ URL は Vanish または Redis によってキャッシュされるため、名前は _ページキャッシュ中毒_.

この種の攻撃は、Web サーバーログにエラーを生じさせないので、検出が困難な場合があります。

このソリューションは、次のコマースバージョンに適用されます。

- 2.0.10 以降
- 2.1.2 以降

>[!INFO]
>
>このトピックは、経験豊富な IIS 管理者を対象としています。

## 説明

この問題は、IIS サーバーで URL の書き換えが有効になっており、要求が Varnish または Redis キャッシュサービスに到達する前に次の HTTP ヘッダーのいずれかが変更される場合に発生します。

- `X-Rewrite-Url`
- `X-Original-Url`
- `IIS-wasurlrewritten`
- `Unencoded-URL`
- `Orig-path-info`

これらのヘッダーを変更すると、結果の URL とコンテンツがキャッシュされ、潜在的な脆弱性が発生する可能性があります。

## 解決策

の IIS サーバー設定に基づいて、前のすべてのヘッダーの値を削除するオプションが用意されています。 `Enable_IIS_Rewrites`.

- If `Enable_IIS_Rewrites` が `0`の場合、ヘッダーの値は削除されます。
- If `Enable_IIS_Rewrites` が `1`の場合、ヘッダーの値はそのまま残ります。

>[!WARNING]
>
>次に `Enable_IIS_Rewrites` から `1`を指定する場合、要求が IIS Web サーバーに到達する前に、前のヘッダーの値を変更しないようにする必要があります。
