---
title: 概要： [!DNL Quality Patches Tool]  （QPT） v1.1.50
description: このサブセクションでは、 [!DNL Quality Patches Tool]  （QPT） v1.1.50で使用可能なパッチによって修正された問題について詳しく説明します。
feature: Tools and External Services
role: Admin, Developer
exl-id: 4e136531-6bd4-4294-9a5a-66d19eb136db
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# 概要：[!DNL Quality Patches Tool] （QPT） v1.1.50

このサブセクションでは、[!DNL Quality Patches Tool] （QPT） v1.1.50で利用可能なパッチによって修正された問題について詳しく説明します。

QPT v1.1.50には、次のパッチが含まれています。

1. **ACSD-59280**: 2.4.4-pX バージョンのインストール時にエラー&#x200B;*未定義のメソッド ReflectionUnionType::getName （）*&#x200B;への呼び出しが発生する問題を修正します。
1. **ACSD-45049**：管理者のweb サイト スコープに従って、顧客&#x200B;*[!UICONTROL Is required]*&#x200B;属性設定が正しく機能しない問題を修正します。
1. **ACSD-46938**: `setup:upgrade`中のDB トリガーの再作成のパフォーマンスに関する問題を修正します。
1. **ACSD-48210**：特定のストアビューで&#x200B;*[!UICONTROL website scope]*&#x200B;属性を更新すると、グローバルスコープの属性値が上書きされる問題を修正します。
1. **ACSD-54887**：顧客セッションの有効期限が切れ、*[!UICONTROL Persistent Shopping Cart]*&#x200B;が有効になった後、顧客の買い物かごがクリアされる問題を修正します。
1. **ACSD-58141**: [!UICONTROL L2 Redis cache]が有効になっていて、お客様が管理者から更新された場合に、ログインのお客様のストアフロント領域のPOST リクエストで`PHPSESSID`が再生成される問題を修正します。
1. **ACSD-58352**: リクエストヘッダーにデフォルト以外のストアビューが指定されている場合に、デフォルトのストアビューの戻り属性ラベルがGraphQL APIを介して返される問題を修正しました。
1. **ACSD-58442**：幅&#x200B;*768px*&#x200B;のデバイスがモバイルとして扱われ、メニューとヘッダーがデスクトップではなくモバイルビューで読み込まれる問題を修正します。
1. **ACSD-58790**: [!DNL Chrome]のモバイルビューで商品詳細ページ画像に表示される&#x200B;*ピンチからズーム*&#x200B;機能を修正しました。
1. **ACSD-59036**：下限と上限の両方が&#x200B;*$0*&#x200B;に等しい製品価格を読み込む際に発生する例外を修正します。
1. **ACSD-59229**：リクエストの[!UICONTROL X-Magento-Vary]の古い値が原因で、顧客グループに関連する情報が間違ったセグメントに保存される問題を修正します。
1. **ACSD-59378**：読み込み中にストアレベル URLの書き換えが正しく更新されない問題を修正します。
1. **ACSD-59514**: [!DNL Page Builder]を使用する管理領域のフォームで、*[!DNL Page Builder]がロックを解除せずに5秒間レンダリングされていた問題を修正します。* フォーム送信後にブラウザーコンソールでエラーが発生し、変更内容を保存できません。
1. **ACSD-60303**: HTMLの縮小が有効になっている場合に管理者からの注文を配置できない問題を修正します。
1. **ACSD-60441**: バックエンドから生成された統合アクセストークンを使用する場合に、`V1/customers REST API` エンドポイントを介して顧客を更新する際の問題を修正します。

左側のメニューを使用して、特定のパッチページに移動します。
