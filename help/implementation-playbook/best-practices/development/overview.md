---
title: 実装開発フェーズ
description: Adobe Commerceプロジェクトの開発段階に関する実装のベストプラクティスについて説明します。
source-git-commit: c717d45525c7893fa2c38183326534e0fa4ee0c6
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---


# 開発段階

開発フェーズには、次のアクティビティが含まれます。

- ローカルおよびステージング環境の設定
- スプリント計画
- チケットの実行
- トラブルシューティング
- コードのレビュー、結合、テスト
- スプリントのレビュー
- 顧客のサインオフ

以下の節では、開発フェーズに関するベストプラクティス情報を示します。

## アプリケーションの開発

### コードのレビュー、結合、テスト

- ガイドラインと標準

<!--Assets not yet integrated
  - [Development best practices](https://wiki.corp.adobe.com/x/nT4ykw)
  - [Code Review](https://wiki.corp.adobe.com/x/qT4ykw)
  - [Debugging Magento 2](https://wiki.corp.adobe.com/x/nz4ykw) (wiki)
-->
- [CSS および JS ファイルの最適化](optimize-css-js-files.md)
- [非公開コンテンツブロックのベストプラクティス](private-content-block-configuration.md)

- カスタムコードを追加
   - [拡張機能開発者向けのベストプラクティス](https://developer.adobe.com/commerce/php/best-practices/)

<!--Assets not yet integrated

  - [Best practices for theme development](https://wiki.corp.adobe.com/pages/viewpage.action?spaceKey=MAGPS&title=Best+Practices+for+Theme+Development)
  - [Module basis](https://wiki.corp.adobe.com/x/kz4ykw) (wiki) — Develop custom modules
  - [Exception Handling](https://wiki.corp.adobe.com/x/nz4ykw)
  - [Custom code copyrights](https://wiki.corp.adobe.com/x/lj4ykw)
- Source control and package management - wiki articles
  - [Code management - Git vs. Composer](https://wiki.corp.adobe.com/x/pz4ykw)
  - [Git branching strategy](https://wiki.corp.adobe.com/display/MAGPS/Git+Branching+Strategy)
  - [Composer development](https://wiki.corp.adobe.com/x/mD4ykw)
  - [Composer patching](https://wiki.corp.adobe.com/x/mj4ykw)
  - [Composer project structure](https://wiki.corp.adobe.com/x/mT4ykw)
  - [Composer tips and tricks](https://wiki.corp.adobe.com/x/lz4ykw)
-->

## Platform とサービス

- [画像の最適化に Fastly を使用](image-optimization.md)

### ローカルおよびステージング環境の設定

- [クラウドインフラストラクチャ上の開発ワークフロー](https://devdocs.magento.com/cloud/architecture/pro-develop-deploy-workflow.html)  — クラウドガイドから追加

## コード、結合、テスト

- [ビルドとデプロイメントのベストプラクティス](https://devdocs.magento.com/cloud/reference/discover-deploy.html#best-practices)
- [静的コンテンツのデプロイメント — クラウド](static-content-deployment.md)
- [CSS および JS ファイルの最適化](optimize-css-js-files.md)
- [よりレスポンシブなサイトに向けて画像を最適化する](image-optimization.md)
- [クラウドインフラストラクチャ上のAdobe Commerceのベストプラクティスのトラブルシューティン&#x200B;グ](troubleshooting.md)
- [データベーステーブルを変更するタイミングと方法を理解す&#x200B;る](modifying-core-and-third-party-tables.md)
