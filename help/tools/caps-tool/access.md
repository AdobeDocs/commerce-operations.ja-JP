---
title: アクセス方法  [!DNL Cloud Automation Patching Service (CAPS)]
description: ' [!DNL Cloud Automation Patching Service (CAPS)] のアクセス方法と使用方法について説明します。'
hide: true
hidefromtoc: true
source-git-commit: ca388bd78affd4def19a5539d8529f2563d35e8c
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 1%

---

# [!DNL Cloud Automation Patching Service (CAPS)] へのアクセス方法

## 前提条件

[!DNL CAPS] では、Adobe Commerce Cloud の役割ベースのアクセス制御を使用します。 Cloud Console のアクセスレベルによって、[!DNL CAPS] で実行できる操作が決まります。

### [!DNL CAPS] を使用できるユーザー

* **プロジェクト管理者** – すべての環境でパッチを適用または元に戻すことができます。
* **投稿者** – 割り当てられた環境にパッチを適用したり、元に戻したりできます。
* **ビューア** - プロジェクトと環境のみを表示できます。アクションは許可されません

### プロジェクトへのアクセスをリクエストする方法

[!DNL CAPS] ユーザーインターフェイスにプロジェクトが表示されない場合は、適切なユーザーにアクセス権をリクエストする必要があります。

* プロジェクトのアカウント所有者またはプロジェクト管理者に連絡してください
* Cloud Console から適切な役割が付与されます
* アクセス権が付与されたら、Cloud Console にログインして [!DNL CAPS] を使用できます

>[!NOTE]
>
>[!DNL CAPS] は Adobe Commerce Cloud と同じ権限モデルに従うので、Cloud Console のアクセスレベルによって、[!DNL CAPS] で実行できる操作が決まります。

## [!DNL CAPS] へのアクセス

CAPS ツールは、[https://supportinsights.adobe.com/commerce/](https://supportinsights.adobe.com/commerce/) の Site-Wide Analysis Tool ダッシュボードから使用できます。 「パッチ適用の自動化」タブで、プロジェクトと環境を選択できます。

1. Site-Wide Analysis Tool （[https://supportinsights.adobe.com/commerce/](https://supportinsights.adobe.com/commerce/)）に移動します。
1. インターフェイスの「[!UICONTROL Patching Automation]」タブをクリックします。
1. パッチを適用するプロジェクトと環境を選択します。
1. 使用可能なパッチとその互換性ステータスを確認します。
1. 適用または復帰するパッチを選択します。

## 実稼動環境へのアクセス

実稼動環境の場合は、次の追加の保護機能が適用されます。

* **メンテナンスモード** – 有効にする必要があります
* **Cron ジョブ** – 無効にする必要があります
* **確認ダイアログ** – 続行する前に完了する必要があります

>[!IMPORTANT]
>
>実稼動環境のパッチ適用には、偶発的な中断を防ぐための適切な準備と保護機能が必要です。

## 関連トピック

* [キャップの概要](intro.md)
* [ワークフロー](workflow.md)
* [ベストプラクティス](best-practices.md)
* [トラブルシューティング](troubleshooting.md)
