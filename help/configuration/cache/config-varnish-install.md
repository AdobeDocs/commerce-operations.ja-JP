---
title: ワニスを取り付ける
description: Vanish のインストールに関するアドバイスを参照してください。
feature: Configuration, Cache
exl-id: e1881a85-3965-42d9-a46f-c2f5f20fbacc
source-git-commit: ec3ab7e3c6c3835e73653b0d4f74aadc861016d3
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 0%

---

# ワニスを取り付ける

Vanish ソフトウェアのインストールは、このガイドの範囲外です。 Vanish のインストールの詳細については、次を参照してください。

- [インストールガイド](https://www.varnish-software.com/developers/tutorials/installing-varnish-ubuntu/)
- [ワニスの取り付けガイド](https://www.varnish-cache.org/docs)
- [Vanish (Tecmint) の取り付け方法](https://www.tecmint.com/install-varnish-cache-web-accelerator/)

>[!INFO]
>
>このトピックは、CentOS および Apache 2.4 の Vanrish 向けに記述されています。異なる環境で Vanish を設定する場合、一部のコマンドは異なる可能性があります。 詳しくは、前述のドキュメントを参照してください。
>
>SAINT モードなどの Vanish モジュール (vmods) をインストールする場合は、パッケージからインストールするのではなく、コードをコンパイルして Vanish をインストールする必要があります。 詳しくは、 [SAINT モード](config-varnish-advanced.md#saint-mode) を参照してください。

## Vanish のバージョンを確認する

ターミナルを開き、次のコマンドを入力して Vanish のバージョンを表示します。

```bash
varnishd -V
```

次を確認します。 [Adobe CommerceとMagento Open Sourceのサポート](../../installation/system-requirements.md) 続行する前にインストールされているバージョンの Vanrish。 サポートされていないバージョンを実行している場合は、サポートされているバージョンにアップグレードする必要があります。 詳細は、Vanish のインストールに関するドキュメントを参照してください。
