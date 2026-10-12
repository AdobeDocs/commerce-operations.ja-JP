---
title: Varnishのインストール
description: Adobe Commerce キャッシュのVarnish インストール要件について説明します。 インストールリソースと設定ガイダンスを確認します。
feature: Configuration, Cache
exl-id: e1881a85-3965-42d9-a46f-c2f5f20fbacc
badgePaas: label="オンプレミス" type="Informative" url="https://experienceleague.adobe.com/ja/docs/commerce/user-guides/product-solutions" tooltip="Adobe Commerce オンプレミス プロジェクトにのみ適用されます。"
autotag-review: '2026-06-22T21:26:58.525Z'
TQID: 'https://experienceleague.adobe.com/Cvy4Qsi-5Fom1t5wqNlq1SiSs4Bb8-DPsWrGfapWfSc'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
    internal-label: Commerce on Prem
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
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
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%
---
# Varnishのインストール

{{varnish-config-cloud}}

Varnishのインストールは、このガイドの範囲外です。 このトピックでは、サポートされているVarnish バージョンと、Varnishの背後で動作するAdobe Commerce オリジンのサーバーを前提としています。 このガイドの例では、nginxをオリジン web サーバーとして使用しています。

- [インストールガイド](https://www.varnish-software.com/developers/tutorials/installing-varnish-ubuntu/)
- [Varnish インストールガイド](https://www.varnish-cache.org/docs)
- [Varnish （Tecmint）のインストール方法](https://www.tecmint.com/install-varnish-cache-web-accelerator/)

>[!INFO]
>
>Saint モードなどのVarnish モジュール（vmod）をインストールする場合は、パッケージからインストールするのではなく、コードをコンパイルしてVarnishをインストールする必要があります。 詳しくは、[Saint mode](config-varnish-advanced.md#saint-mode)を参照してください。

## Varnish バージョンを確認します

ターミナルを開き、次のコマンドを入力してVarnishのバージョンを表示します。

```shell
varnishd -V
```

続行する前に、[Adobe CommerceがインストールされているバージョンのVarnishを](../../installation/system-requirements.md) サポートしていることを確認してください。 サポートされていないバージョンを実行している場合は、サポートされているバージョンにアップグレードする必要があります。 詳しくは、Varnishのインストールドキュメントを参照してください。
