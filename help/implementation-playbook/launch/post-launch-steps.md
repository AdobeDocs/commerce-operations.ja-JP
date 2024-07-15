---
title: Postの起動手順
description: ローンチ後のチェックリストを使用して、Adobe Commerce サイトのスムーズな実装を確認します。
exl-id: 0c3162d9-6475-4b34-9278-e5aea39bd0f9
feature: Deploy
source-git-commit: ce41158f900fad27e3e7b8157f5c64ac988bbabf
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 0%

---

# Postの起動手順

Web サイトが実稼働したら、サイトが正しく起動されたことを確認するために、これらのアクティビティをできるだけ早く実行します。

- Up-time Monitoring Tool （New Relic）を有効にし、チェックをアクティブ化し、サイトをモニタリングして、すべてのサービスとアクセスが緑色で表示されるようにします
- Adobe Commerce セキュリティスキャンを定期的に有効にする
- クラスターをライブとしてタグ付けし、サポートチケットを作成して高 SLA 監視を有効にします
- カットオーバーが完了したらすぐに、CSE （カスタマーサクセスエンジニア）と TAM （テクニカルアカウントマネージャー）が次のタスクを実行します。
   - クラスターをAdobe Commerce クライアントの高 SLA としてタグ付けし、サポートチケットを作成してアクティブ化します
   - **内部** Pingdom チェックを有効にしてドメイン名を確認します（Pingdom へのパブリックアクセスは利用できません）。
   - 監視状態を確認し、すべての項目が緑色になっていることを確認します
   - 運用開始日に、保証の期間とパラメーターを関係者にメールで知らせる

![ 立ち上げプロセスのフェーズ 4 を示す図 ](../../assets/playbooks/launch-steps-4.svg)
