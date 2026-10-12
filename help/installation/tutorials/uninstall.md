---
title: Adobe Commerceのアンインストールまたは再インストール
description: Adobe Commerceのオンプレミスインストールをアンインストールして再インストールするには、次の手順に従います。
exl-id: fbaeee2c-8da0-4c89-a6d1-882a65014520
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
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
source-wordcount: '284'
ht-degree: 0%
---
# Adobe Commerceのアンインストールまたは再インストール

これらのコマンドを使用する前に、アプリケーションを[&#x200B; インストールする必要があります](../tutorials/install.md)。

## アプリケーションの更新

アプリケーションを更新するには：

* アーカイブからソフトウェアをインストールした場合、または「composer-create-project」を使用した場合は、[&#x200B; アップグレードガイド &#x200B;](../../upgrade/overview.md)を参照してください。
* 提供元の開発者（つまり、`git clone`を使用している）の場合は、[&#x200B; アプリケーションの更新](../../upgrade/developer/git-installs.md)を参照してください。

## アプリケーションの再インストール

コマンドラインからアプリケーションを再インストールする方法は、役割によって異なります。

* アーカイブからソフトウェアをインストールした場合、または「composer-create-project」を使用した場合は、[&#x200B; インストール依存関係の更新](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies)を参照してください。
* 提供開発者（つまり、`git clone`を使用し始めた）の場合は、[&#x200B; インストール依存関係の更新](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies)を参照してください。

## アプリケーションのアンインストール

アプリケーションをアンインストールすると、データベースが削除および復元され、デプロイメント設定が削除され、`var`の下のディレクトリがクリアされます。

アプリケーションをアンインストールするには、次のコマンドを入力します。

```shell
bin/magento setup:uninstall
```

アンインストールが正常に完了したことを確認するには、次のメッセージが表示されます。

```text
[SUCCESS]: Magento uninstallation complete.
```

## 必要に応じて、生成されたファイルを保持

デフォルトでは、`bin/magento setup:upgrade`はコンパイルされたコードとキャッシュをクリアします。 通常、`bin/magento setup:upgrade`を使用してコンポーネントを更新します。各コンポーネントには異なるコンパイル済みクラスが必要になる場合があります。

ただし、状況によっては（特に実稼動環境にデプロイする場合）、コンパイル済みコードのクリアは時間がかかることがあるため、避ける必要があります。 （キャッシュはクリアされたままです）。 コンパイル済みコードを&#x200B;*クリアせずにデータベーススキーマとデータ*&#x200B;を更新するには、次のように入力します。

```shell
bin/magento setup:upgrade --keep-generated
```

>[!WARNING]
>
>オプションの`--keep-generated` オプションは、経験豊富なシステムインテグレーター&#x200B;*のみ*&#x200B;が限られた状況で使用する必要があります。 このオプションは、開発環境で&#x200B;*never*&#x200B;を使用する必要があります。 このオプションのパラメーターを不適切に使用すると、コードの実行中にエラーが発生する可能性があります。

## アプリケーションのインストール

* [コマンドラインを使用してインストール](../advanced.md)
