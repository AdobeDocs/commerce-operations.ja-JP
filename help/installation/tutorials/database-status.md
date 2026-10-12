---
title: データベースのステータスの確認
description: Adobe Commerce データベースのステータスを確認するには、次の手順に従います。
exl-id: 33d9b30a-4504-4955-b11a-0a642f23209b
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
source-wordcount: '104'
ht-degree: 3%
---
# データベースのステータスの確認

このコマンドを実行する前に、[&#x200B; デプロイメント設定を作成または更新する必要があります](deployment.md)。

## コマンドの使用

データベースのステータスを確認します。

```shell
bin/magento setup:db:status
```

このコマンドには引数またはオプションがありません。

出力の例は次のとおりです。

```text
All modules are up to date.
```

このコマンドは、次のいずれかの終了コードを返します。

| 終了コード | 説明 | 推奨アクション |
|--------------|--------------|---------------|
| 0 | 標準 | なし |
| 1 | 一部のモジュールでは、データベースよりも新しいまたは古いコードバージョンを使用します | [`magento setup:upgrade`](database-upgrade.md)を実行してデータベース スキーマを更新し、アプリケーション ルート ディレクトリから`composer update`を実行してコンポーネントの依存関係を更新します |
| 2 | `magento setup:upgrade`が必要です | データベース スキーマを更新する[`magento setup:upgrade`](database-upgrade.md) |
