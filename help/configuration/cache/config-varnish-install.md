---
title: ワニスをインストール
description: ワニスのインストールに関するアドバイスを参照してください。
feature: Configuration, Cache
exl-id: e1881a85-3965-42d9-a46f-c2f5f20fbacc
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '158'
ht-degree: 0%

---

# ワニスをインストール

ワニス ソフトウェアのインストールはこのガイドの範囲外です。 Varnish のインストールの詳細については、次を参照してください。

- [ インストールガイド ](https://www.varnish-software.com/developers/tutorials/installing-varnish-ubuntu/)
- [ ワニス取り付けガイド ](https://www.varnish-cache.org/docs)
- [ ワニス（Tecmint）のインストール方法 ](https://www.tecmint.com/install-varnish-cache-web-accelerator/)

>[!INFO]
>
>このトピックは、CentOS および Apache 2.4 の Varnish 用に記述されています。別の環境で Varnish を設定している場合、一部のコマンドは異なる可能性があります。 詳しくは、前のドキュメントを参照してください。
>
>Saint モードなどの Varnish モジュール（vmod）をインストールする場合は、パッケージからインストールするのではなく、コードをコンパイルして Varnish をインストールする必要があります。 詳しくは、[ セイント モード ](config-varnish-advanced.md#saint-mode) を参照してください。

## Varnish バージョンを確認します。

ターミナルを開き、次のコマンドを入力して Varnish のバージョンを表示します。

```bash
varnishd -V
```

続行する前に、インストールされているバージョンの Varnish](../../installation/system-requirements.md)[Adobe Commerceがサポートしていることを確認してください。 サポートされていないバージョンを実行している場合は、サポートされているバージョンにアップグレードする必要があります。 詳細については、Varnish のインストール ドキュメントを参照してください。
