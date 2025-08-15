---
title: 概要： [!DNL Quality Patches Tool]  （QPT） v1.1.31
description: ここでは、 [!DNL Quality Patches Tool]  （QPT） v1.1.31 で使用可能なパッチによって修正された問題について詳しく説明します。
feature: Tools and External Services
role: Admin
exl-id: d37c7f05-1bf5-495b-9b9e-ac9dd117a3ab
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 0%

---

# 概要：[!DNL Quality Patches Tool] （QPT） v1.1.31

このサブセクションでは、[!DNL Quality Patches Tool] （QPT） v1.1.31 で使用可能なパッチによって修正された問題について詳しく説明します。

QPT v1.1.31 には、次のパッチが含まれています。

1. **ACSD-50817**：見積もりテーブルの `sales_clean_quotes` 列と `store_id` 列に複合インデックスを追加することで、cron ジョブ `updated_at` ータの実行速度を向上させるように最適化します。
1. **ACSD-50345**：支払い失敗の送信後に [!DNL Google reCAPTCHA v2] が再読み込みされない、[!DNL Google reCAPTCHA v3 Invisible] がチェックアウトで機能しない、注文できない、イベントがトリガーされなかった問題 [!UICONTROL PlaceOrder] 修正しました。
1. **ACSD-49392**：バンドルされた製品の部分払い戻しの後に、注文のステータスがクローズに変更される問題を修正しました。
1. **ACSD-51036**：同時 REST API 呼び出し中の競合状態によって、[!UICONTROL Items Ordered] テーブルの出荷ステータス情報が上書きされる問題を修正しました。
1. **ACSD-50858**：カードの支払いに失敗した後、クーポンが誤って使用済みとしてマークされる問題を修正しました。

左側のメニューを使用して、特定のパッチページに移動します。
