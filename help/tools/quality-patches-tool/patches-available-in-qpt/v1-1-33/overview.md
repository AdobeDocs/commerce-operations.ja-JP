---
title: 概要： [!DNL Quality Patches Tool]  （QPT） v1.1.33
description: ここでは、 [!DNL Quality Patches Tool]  （QPT） v1.1.33 で使用可能なパッチによって修正された問題について詳しく説明します。
feature: Tools and External Services
role: Admin
exl-id: 31812668-1d24-4da6-992f-981c259e00da
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# 概要：[!DNL Quality Patches Tool] （QPT） v1.1.33

このサブセクションでは、[!DNL Quality Patches Tool] （QPT） v1.1.33 で使用可能なパッチによって修正された問題について詳しく説明します。

QPT v1.1.33 には、次のパッチが含まれています。

1. **ACSD-50478**: DB ダンプにトリガーと区切り文字 SQL コマンドが含まれている場合に、データベース ロールバック コマンドを修正します。
1. **ACSD-50512**：次のエラーを修正しました：*ダウンロード可能なリンクは製品に関連していません。 リンクを確認して、もう一度試してください。ダウンロ* ド可能な製品のステージング更新の開始日を更新する際に発生するエラー。
1. **ACSD-50949**:[!UICONTROL Advanced Search] の価格フィルターを SKU フィルターと一緒に使用すると、適切な結果が返されない問題を修正しました。
1. **ACSD-51645**：拡張 `Magento_OfflineShipping` 能が無効になっている場合に、新しい [!UICONTROL Cart Price Rule] を保存する際にスローされるエラーを修正します。
1. **ACSD-50895**:[!DNL Google Analytics] 4 GTM が設定されていない場合に、[!DNL Google Analytics] 3 GTM タグが起動されない問題を修正しました。
1. **ACSD-51102**：スケジュールされた更新によってルールが有効になっている場合に、多数の製品に適用されるカタログルールが正しくインデックス化されない問題を修正しました。
1. **ACSD-50368**：非同期 REST API または非同期バルク REST API を使用して顧客を作成する際に、顧客の `group_id` が無視される問題を修正しました。
1. **ACSD-51497**：顧客がドロップダウンタイプのい [!UICONTROL Custom Attribute] れかでカタログページを並べ替えることができない問題を修正しました。
1. **ACSD-51408**：注文項目のステータスが正しく [!UICONTROL Backordered] に設定されない問題を修正しました。
1. **ACSD-51735**：商品在庫が *0* の場合に、注文項目のステータスが正しく [!UICONTROL Ordered] に設定されない問題を修正しました。
1. **ACSD-51792**:[!DNL Google Tag Manager] 4 が有効な場合に、ページにインプレッションイベントが表示されない問題を修正しました。
1. **ACSD-51471**：自身にスケジュール済みアップデートがあるシンプルな製品を使用しているバンドル製品について、管理者ユーザーがスケジュール済みアップデートを保存できない問題を修正しました。
1. **ACSD-51700**：管理画面でダウンロード可能な製品編集ページのストアビューを切り替えるときに発生するエラーを修正しました。
1. **ACSD-51120**：ステージングアップデートにより更新されたGET ブロックを含んだCMS ページのGraphQL CMS リクエストのキャッシュがクリアされない問題を修正しました。
1. **ACSD-51240**：会社登録フォームで登録した場合に、アップロードされたファイルが見つからない問題を修正しました。
1. **ACSD-51907**：制限付き管理者ユーザーが、オフラインでの払い戻しでクレジットメモを作成できない問題を修正しました。
1. **ACSD-52148**:[!UICONTROL Google V3 reCAPTCHA Admin] ログインが失敗することがある問題を修正しました。
1. **ACSD-51431**：変更ログに新しいエントリがない場合でもインデクサーのステータスが機能する問題を修正しました。
1. **ACSD-51892**：配置中に設定ファイルが複数回読み込まれるパフォーマンスの問題を修正しました。

左側のメニューを使用して、特定のパッチページに移動します。
