---
title: Varnishのインストール
description: Adobe Commerce キャッシュのVarnish インストール要件について説明します。 インストールリソースと設定ガイダンスを確認します。
feature: Configuration, Cache
exl-id: e1881a85-3965-42d9-a46f-c2f5f20fbacc
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 0%

---

# Varnishのインストール

Varnish ソフトウェアのインストールは、このガイドの範囲を超えています。 Varnishのインストールについて詳しくは、次を参照してください。

- [インストールガイド](https://www.varnish-software.com/developers/tutorials/installing-varnish-ubuntu/)
- [Varnish インストールガイド](https://www.varnish-cache.org/docs)
- [Varnish （Tecmint）のインストール方法](https://www.tecmint.com/install-varnish-cache-web-accelerator/)

>[!INFO]
>
>このトピックは、CentOSおよびApache 2.4でVarnishに対して記述されています。 Varnishを別の環境で設定する場合、一部のコマンドは異なる可能性があります。 詳しくは、前述のドキュメントを参照してください。
>
>Saint モードなどのVarnish モジュール（vmod）をインストールする場合は、パッケージからインストールするのではなく、コードをコンパイルしてVarnishをインストールする必要があります。 詳しくは、[Saint mode](config-varnish-advanced.md#saint-mode)を参照してください。

## Varnish バージョンを確認します

ターミナルを開き、次のコマンドを入力してVarnishのバージョンを表示します。

```shell
varnishd -V
```

続行する前に、[Adobe CommerceがインストールされているバージョンのVarnishを](../../installation/system-requirements.md) サポートしていることを確認してください。 サポートされていないバージョンを実行している場合は、サポートされているバージョンにアップグレードする必要があります。 詳しくは、Varnishのインストールドキュメントを参照してください。
