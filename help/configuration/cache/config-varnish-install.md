---
title: ワニスを取り付ける
description: Vanish のインストールに関するアドバイスを参照してください。
source-git-commit: c65c065c5f9ac2847caa8898535afdacf089006a
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 0%

---


# ワニスを取り付ける

Vanish ソフトウェアのインストールは、このガイドの範囲外です。 Vanish のインストールの詳細については、次を参照してください。

- [インストールガイド](https://www.varnish-software.com/developers/tutorials/installing-varnish-ubuntu/)
- [ワニスの取り付けガイド](https://www.varnish-cache.org/docs)
- [Vanish (Tecmint) の取り付け方法](https://www.tecmint.com/install-varnish-cache-web-accelerator/)

>[!INFO]
>
>このトピックは、CentOS と Apache 2.4 で Vanrish を使用するために記述されています。Vanrish を別の環境で設定する場合、一部のコマンドが異なる可能性があります。 詳しくは、前述のドキュメントを参照してください。
>
>SAINT モードなどの Vanish モジュール (vmods) をインストールする場合は、パッケージからインストールするのではなく、コードをコンパイルして Vanish をインストールする必要があります。 詳しくは、 [SAINT モード](config-varnish-advanced.md#saint-mode) を参照してください。

## Vanish バージョンを確認する

ターミナルを開き、次のコマンドを入力して Vanish のバージョンを表示します。

```bash
varnishd -V
```

次に例を示します。

```terminal
varnishd (varnish-6.3.2 revision 199de9b)
Copyright (c) 2006 Verdens Gang AS
Copyright (c) 2006-2019 Varnish Software AS
```

続行する前に、バージョンが 6.x であることを確認してください。 6.x より前のバージョンを実行している場合は、サポートされているバージョンにアップグレードする必要があります。 詳細は、Vanish のインストールに関するドキュメントを参照してください。
