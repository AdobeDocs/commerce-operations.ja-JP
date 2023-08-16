---
title: インストールの確認
description: オンプレミスのAdobe CommerceまたはMagento Open Sourceのインストールが正常に完了したことを確認するには、次の手順に従います。
exl-id: 0bd7ec01-c616-4384-ae26-db2ce3668caf
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 0%

---

# インストールの確認

Web ブラウザーのストアフロントに移動します。 例えば、インストールベース URL が `http://www.example.com`を使用する場合は、ブラウザーのアドレスまたはロケーションバーに入力します。

次の図は、ストアフロントページのサンプルを示しています。 次のように表示される場合は、インストールは成功しています。

![Luma テーマを使用したストアフロント](../../assets/installation/install-success_store-luma.png)

## ストアフロントを検証します（サンプルデータがありません）

Web ブラウザーのストアフロントに移動します。 例えば、インストールベース URL が `http://www.example.com`を使用する場合は、ブラウザーのアドレスまたはロケーションバーに入力します。

次の図は、ストアフロントページのサンプルを示しています。 次のように表示される場合は、インストールは成功しています。

![インストールが成功したことを確認するストアフロント](../../assets/installation/install-success_store.png)

ページに `404 (Not Found)` エラーが発生したか、スタイルが表示されません。詳しくは、 [トラブルシューティング](https://support.magento.com/hc/en-us/articles/360032994352).

## 管理者の確認

Web ブラウザーで管理者に移動します。 例えば、インストールベース URL が `http://www.example.com`の場合、Admin URI は `admin_au1nT`，と入力します。 `http://www.example.com/admin_au1nT` をクリックします。

( 管理 URI は、 `backend-frontname` インストールパラメータ )。

プロンプトが表示されたら、管理者としてログインします。

次の図は、管理ページのサンプルを示しています。 次のように表示される場合は、インストールは成功しています。

![インストールが成功したことを確認する管理者](../../assets/installation/install_success_admin.png)

ページにスタイルが表示されない場合は、 [トラブルシューティング](https://support.magento.com/hc/en-us/articles/360032994352).

次のような 404（見つかりません）エラーが表示された場合は、 [ブラウザでAdobe Commerceにアクセスする際に PHP バージョンエラーが発生した、または 404 が発生した](https://support.magento.com/hc/en-us/articles/360033117152).

`The requested URL /magento2index.php/admin/admin/dashboard/index/key/0c81957145a968b697c32a846598dc2e/ was not found on this server.`
