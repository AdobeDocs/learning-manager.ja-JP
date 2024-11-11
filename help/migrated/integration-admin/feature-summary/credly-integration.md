---
jcr-language: en_us
title: 信心深く
description: 様々なソーシャルメディアチャネルでプラットフォームから外部バッジを管理および共有するためのALMとのCredlyの統合について説明します
contentowner: chandrum
source-git-commit: a27c1566678d697512a75d94804b8804b5dc9b2b
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# 信心深く

[Credly](https://info.credly.com/)は、学習者と組織がバッジや資格認定などの専門的な成果を獲得、共有、および確認できるようにするデジタル資格情報プラットフォームです。 学習者は、ソーシャルメディアやその他の場所にあるCredlyプロファイルを通じてバッジを管理および共有できます。

## 前提条件

組織のCredlyアカウントを設定します。 Adobe Learning Managerで電子メールIDを使用して、学習者をCredlyに追加します。 これにより、学習者はCredlyとAdobe Learning Managerにバッジを表示できます。

## Adobe Learning ManagerへのCredlyコネクタの追加

Adobe Learning ManagerにCredlyコネクタを追加するには、次の手順に従います。

1. **[!UICONTROL 統合管理者]**&#x200B;としてログインします。
2. **[!UICONTROL Credly]** > **Connect**&#x200B;を選択して、**[!UICONTROL Credly]**&#x200B;コネクタをAdobe Learning Managerに追加します。

   ![](assets/connector-credly.png)
   _信頼できるコネクタの追加_

3. **[!UICONTROL 接続名]**&#x200B;を入力します。
4. **[!UICONTROL 組織ID]**&#x200B;と&#x200B;**[!UICONTROL 認証トークン]**&#x200B;を入力します。

   >[!NOTE]
   >
   >Credlyの各バッジには、組織IDと認証トークンが付属しています。 これらの値をCredlyからコピーします。

5. **[!UICONTROL ホスト名]**&#x200B;を入力し、**[!UICONTROL 接続]**&#x200B;を選択します。

## Credlyからバッジを移行

Adobe Learning Managerのbadge.csvを使用すると、既存のLMSまたは外部システムからバッジを移行できます。 badge.csvが2つの新しい列で更新されました。

* 外部バッジID
* 外部バッジプロバイダー。

外部バッジIDは、CredlyプラットフォームのバッジテンプレートIDを参照し、外部バッジプロバイダーはCredlyです。 badge.csvにこれらの値を追加し、[移行マニュアル](https://experienceleague.adobe.com/en/docs/learning-manager/using/integration/migration-manual#migrationprocedure)に記載されている手順に従ってcsvを移行します。

## スキルの作成 – 管理者

バッジをAdobe Learning Managerに読み込むと、管理者はスキルとしてこのバッジを作成できます。 スキルの作成方法については、[スキルの作成と変更](https://experienceleague.adobe.com/en/docs/learning-manager/using/admin/skills-levels)を参照してください。

### 学習オブジェクトにスキル/バッジを割り当てる – 作成者

作成者/管理者は、これらのCredlyで読み込まれたALMバッジを（スキルだけでなく）コース、学習パス、資格認定に割り当てることができます。これらの学習目標の使用時に、バッジが達成され、CredlyおよびALMアプリで表示できます。

学習者はCredlyにログインし、Credlyプラットフォームでバッジを確認できます。 Credlyから、LinkedInやその他のソーシャルメディアなどの外部プラットフォームでバッジを共有できます。

