---
title: 概要： [!DNL Quality Patches Tool]  （QPT） v1.1.78
description: このサブセクションでは、 [!DNL Quality Patches Tool]  （QPT） v1.1.78で使用可能なパッチによって修正された問題について詳しく説明します。
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: a26830c032f09a41f857afe2f10b8886fbe495e5
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 0%

---

# 概要：[!DNL Quality Patches Tool] （QPT） v1.1.78

このサブセクションでは、[!DNL Quality Patches Tool] （QPT） v1.1.78で利用可能なパッチによって修正された問題について詳しく説明します。

QPT v1.1.78には次のパッチが含まれています。

1. **[ACP2E-4456](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4456.md)**: GraphQLの突然変異を使用して注文をキャンセルしても、ギフトカードで支払われた注文が完全に「クローズ」ステータスに移行しない問題を修正しました。
1. **[ACP2E-4452](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4452.md)**: [!UICONTROL Quick Order] ページの製品価格に税金が含まれる問題を、税表示設定に関係なく修正します。
1. **[ACP2E-4513](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4513.md)**：期限切れのCAPTCHA画像がシステムから削除されない問題を修正します。
1. **[ACP2E-4448](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4448.md)**: Redisの復旧後にRedisの障害時に行われた設定変更が反映されず、古い値が保持される問題を修正しました。
1. **[ACP2E-4416](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4416.md)**：管理画面で作成したときに顧客報酬ポイントが初期化されない問題を修正します。
1. **[ACP2E-4431](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4431.md)**：再インデックスプロセス中に、ターゲットルールに一致する[!UICONTROL Related Products]が削除される問題を修正します。
1. **[ACP2E-4419](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4419.md)**: ストアフロントでreCAPTCHA v2 （「私はロボットではありません」）の検証が正常に行われた後、チェックアウト時にギフトカードが正しく適用されない問題を修正しました。
1. **[ACP2E-4507](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4507.md)**: GraphQLの変更を通じて行われたお客様のパスワードリセット要求に[!UICONTROL Password Options]設定が適用されない問題を修正します。
1. **[ACP2E-4522](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4522.md)**：複数の買い物かごの結合要求または見積もり保存要求が同時に実行されるときに、`quote_coupons` テーブルで断続的な重複キーエラーが発生する問題を修正します。
1. **[ACP2E-4528](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4528.md)**：顧客アドレスの市区町村検証の問題を修正しました。これにより、スラッシュ（/）文字が使用できるようになり、!、&quot;、#、？などの無効な文字が拒否されるようになりました。
1. **[ACP2E-4535](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4535.md)**：パスワードを忘れたフォームを送信すると、セッションが破棄または再生成され（PHPSESSIDの変更）、ゲストカートがクリアされる問題を修正しました。
1. **[ACP2E-4591](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4591.md)**: 「初回購入者」などの注文数に基づく顧客セグメントが、REST APIを介して注文が行われたときに更新されない問題を修正します。
1. **[ACP2E-4540](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4540.md)**: Fotorama ライブラリが正しく読み込まれず、最初に添付された画像のみが表示される問題を修正しました。
1. **[ACP2E-4555](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4555.md)**:「」を含む最新の電話番号の問題を修正します。 または「/」が正しく検証されていません。
1. **[ACP2E-4565](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4565.md)**: X-Adobe-Company ヘッダーを使用すると、Company GraphQL クエリが「現在のお客様が許可されていません」と返される問題を修正します。
1. **[ACP2E-4609](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4609.md)**：一部の引用符に削除済み製品が含まれている場合に、マイ引用符ページに引用符が表示されない問題を修正しました。
1. **[ACP2E-4613](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4613.md)**：大きなメディアディレクトリ構造によってgettreeの応答が遅くなり、**[!UICONTROL Media Gallery]** ディレクトリツリーの読み込み時間が長くなる問題を修正します。
1. **[ACP2E-4628](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4628.md)**: アカウント共有がグローバルに設定されている場合に、大文字の電子メールアドレスを持つ顧客を読み込むと、未定義の配列キーエラーが発生する問題を修正します。
1. **[ACP2E-4763](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4763.md)**: カタログ価格が税金を含むように設定されている場合に、GraphQL customerOrders クエリで`original_price_including_tax`と`original_row_total_including_tax`の値が膨張して返される問題を修正しました。税金が2回適用されます。
1. **[ACP2E-4732](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4732.md)**：変更ログテーブルの`version_id`列が最大値に達したときに、多数の更新を行った顧客に対して部分的なインデックス作成が停止する問題を修正します。
1. **[ACP2E-4665](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4665.md)**：製品ギャラリーにビデオを含む設定可能な製品の子製品が、REST APIを介して要求されたときに表示されない問題を修正します。
1. **[ACSD-60989](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acsd-60989.md)**：宣言型スキーマを使用して外部キーで列を変更すると、MariaDBでエラーが発生する問題を修正します。

左側のメニューを使用して、特定のパッチページに移動します。
