---
title: '[!DNL Observation for Adobe Commerce]'
description: '[!DNL Observation for Adobe Commerce]とその用途、使用するタイミング、アクセス方法について説明します。'
exl-id: a787be0f-5dd8-4acc-adbf-5cedd96b08d6
feature: Configuration, Observability
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: 4239b8a6-e74f-567d-a7a5-b98b9ead0ea4
    internal-label: Observability
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
source-wordcount: '365'
ht-degree: 0%
---
# [!DNL Observation for Adobe Commerce]

このガイドでは、[!DNL Observation for Adobe Commerce]の全体像を説明します。 使用状況、使用時期、使用方法、問題を確認するための一般的なアプローチ、ツールへのアクセス方法について説明します。

## [!DNL Observation for Adobe Commerce]とは

[!DNL Observation for Adobe Commerce]は、複数のソースからのログデータを組み合わせて、Adobe Commerce サイトのパフォーマンスをより適切に管理し、問題を診断するのに役立つツールです。 アプリケーションのログデータと、[!DNL New Relic observability] プラットフォームのデータを、わかりやすいダッシュボードで視覚的に表示します。 ソリューションは[!DNL New Relic Nerdlets]に基づいています。これは、[!DNL New Relic One]個のプログラマビリティ インターフェイスで構築されたカスタム アプリケーションです。

問題が発生したときに、その問題がどこから発生したのかを把握し、その問題を解決するための知識を得るのに時間がかかることがあります。 Adobeのサポート組織は、問題のトラブルシューティングを行いながら、ログとコマンドライン出力を長年調べることに基づいて構築された部族的な知識を積み重ねてきました。 このツールは、そのような知識を活用して、共通のタイムラインに対する重要なシグナルを特定します。 タイムラインは拡張または縮小でき、ログデータを視覚化して、パフォーマンス管理と問題解決に役立てることができます。

[!DNL Observation for Adobe Commerce]を使用すると、サポートが発生した複雑な問題を分析して、根本原因を特定できます。 さまざまなデータを追跡する代わりに、イベントとエラーを関連付けて時間を費やし、パフォーマンスのボトルネックの原因に関する詳細なインサイトを得ることができます。 このツールは、問題の潜在的な根本原因を特定し、サイトのパフォーマンスを最適に維持するために、サイトが経験する問題のいくつかをより明確に把握することを目的としています。 これには、サイトの問題を引き起こしているかどうか、および何の[!DNL bots]を特定することが含まれます。

## このガイドは誰のためのものでしょうか？

Adobe Commerceサイトのパフォーマンスを最適化して、問題を診断したい販売者とパートナー。 [!DNL Observation for Adobe Commerce]は次の目的で使用できます。

* サイトに問題が発生する前に、共通のタイムラインと情報を比較することで、パフォーマンスが低下している原因を確認することができます。

* 障害時に数百万のログメッセージを探す場所と探すべき場所を把握します。

* ログから重要なエラーメッセージを視覚的に要約することで、データの収集と解析を簡素化できます。

* IP リクエストの頻度、アクセスされたURL、使用されたAPIなど、様々なサービスをまたいで視点を獲得できます。

## [!DNL Observation for Adobe Commerce] デモ

[!DNL Observation for Adobe Commerce]について詳しくは、このビデオをご覧ください。

>[!VIDEO](https://video.tv.adobe.com/v/3410749?captions=jpn&quality=12)
