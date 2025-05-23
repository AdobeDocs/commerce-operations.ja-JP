---
title: コンテンツセキュリティポリシーの概要
description: コンテンツセキュリティポリシーを使用して、Adobe Commerce ストアのセキュリティの態勢を改善する方法を説明します。
exl-id: 81070a09-5f8f-48b1-b542-1443dbd43f5f
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 0%

---

# コンテンツセキュリティポリシーの概要

コンテンツセキュリティポリシー（CSP）は、クロスサイトスクリプティング（XSS）と関連するデータインジェクション攻撃の検出と軽減を支援することで、Adobe Commerceのインストールに対してさらに高度な防御機能を提供できます。 この一般的な攻撃ベクトルは、web サイトを発信元と誤って主張する悪意のあるコンテンツを挿入することで機能します。 悪意のあるコンテンツが読み込まれて実行された後、データの不正な転送が開始される可能性があります。

CSP は、どのコンテンツリソースを信頼できるか、およびどのコンテンツリソースをブロックするかをブラウザーに指示する、標準化された一連のディレクティブを提供します。 慎重に定義されたポリシーを使用して、CSP は、許可リストに登録されたリソースのみを表示するようにブラウザーコンテンツを制限できます。

## 設定

サイト操作の妨げとならないように、CSP は段階的に実装できます。 CSP には、`report-only mode` と `restrict mode` という 2 つの基本的な操作モードがあります。

**レポートのみのモード**：ブラウザーはポリシー違反をレポートするように指示されますが、ポリシー違反は強制されません。 リクエストされたリソースが CSP に違反するたびに、ブラウザーは結果のエラーをコンソールに記録します。 その後、コンソールログを使用して、各違反の原因を調査できます。

発生したすべての CSP エラーを確認し、必要なすべてのリソースが許可リストに登録されるまでポリシーを調整することが重要です。 エラーが発生しなくなったら、`restrict mode` に切り替えても安全です。 そうしないと、CSP の設定が不十分な場合に、多数のコンソールエラーが発生する空白ページがブラウザーに表示される可能性があります。 CSP を適切に設定すると、パフォーマンスに影響を与えずに、許可リストに登録されたコンテンツを配信できます。

**制限モード**：ブラウザーは、すべてのコンテンツポリシーを適用し、公開を許可リストに登録されたリソースに制限するように指示されます。

Adobe Commerce CSP 実装の第 1 段階は、Adobe Commerce 2.3.5 で導入され、デフォルトで `report-only mode` で CSP を使用できるようになりました。  Adobe Commerce 2.4.7 以降では、CSP は、ストアフロントおよび管理領域の支払いページにはデフォルトで `restrict-mode` で設定され、その他のすべてのページには `report-only` モードで設定されます。 対応する CSP ヘッダーには、支払いページの `script-src` ディレクティブ内に `unsafe-inline` キーワードが含まれていません。 また、許可されているのは、ホワイトリストに登録されたインラインスクリプトだけです。

CSP は管理者ではなくサーバーから設定されるので、ほとんどのマーチャントは、適切に設定するためにシステムインテグレーターまたは開発者の支援を必要とします。 [2&rbrace;Commerce PHP デベロッパーガイド ](https://developer.adobe.com/commerce/php/development/security/content-security-policies/) コンテンツセキュリティポリシー _を参照してください。_


## 報告書

デフォルトでは、CSP はブラウザーコンソールにエラーを送信しますが、HTTP リクエストによってエラーログを収集するように設定できます。 さらに、CSP 違反の監視、収集、レポートに使用できるサードパーティのサービスがいくつか用意されています。 CSP 違反は、管理者またはカスタムモジュールの `config.xml` ファイルから URI を追加することで、収集のためにエンドポイントにレポートできます。  [2&rbrace;Commerce PHP Extensions 開発者ガイド ](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#report-uri-configuration) の「Report URI configuration」を参照してください __

[ レポート URI](https://report-uri.io/) は、CSP 違反を監視し、結果をダッシュボードに表示するサービスです。 マーチャントと開発者の両方が、CSP 違反が発生した場合は常にサービスを使用してレポートを受け取ることができます。
