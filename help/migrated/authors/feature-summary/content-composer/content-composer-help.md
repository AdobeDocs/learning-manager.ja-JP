---
title: Adobe Learning Manager Content Composer (Beta)ヘルプ
description: 平易な言葉のプロンプトからパブリッシュ済みのコースまで、Adobe Learning Manager Content Composerがインストラクションデザインを処理するので、影響力の大きいインストラクションコンテンツを作成して、学習者のニーズに集中できます。
contentowner: saghosh
source-git-commit: fc3affc155fd10bd74f4b11175bf76fe64ddf6d4
workflow-type: tm+mt
source-wordcount: '762'
ht-degree: 0%

---


# Adobe Learning Manager Content Composer (Beta)ヘルプ

>[!IMPORTANT]
>
>ベータ版の機能には不具合が含まれている場合があり、いかなる種類の保証も付けずに「現状のまま」提供されます。 Adobeは、ベータ版機能の一般提供の有無について独自の判断を行います。 Adobeは、（Adobeサポートサービスまたはその他の方法による）ベータ版機能を維持、修正、更新、変更、またはその他の方法でサポートする義務を負いません。 ベータ版の機能が一般に公開された場合は、適用される料金を含め、追加の利用条件が適用される場合があります。 ベータ版の機能は、提供の終了を含め、予告なく変更される場合があります。 お客様には、ベータ版機能の中断またはエラーのない機能やパフォーマンスに注意して使用し、いかなる方法でも信頼しないことを推奨します。 したがって、ベータ版機能の使用は、完全にお客様自身の責任で行うものとします。 製品機能および関連ドキュメントは、機能の進化に伴って変更される場合があります。 このドキュメントは、現在のベータ版のエクスペリエンスを反映しているため、最終的な製品ドキュメントまたは完全な製品ドキュメントと見なすことはできません。

## 数分でコンセプトからコースへ

Adobe Learning Manager Content Composerは、わかりやすい言語のプロンプトを、構造化された公開可能なコース（レッスン、評価、メディアを含む）に変換するAIコースオーサリングツールです。インストラクションデザインの経験は必要ありません。

Content Composerは、トレーニングの目標、ソース資料、学習目標について会話を通じて作成者をガイドし、教育的に健全で、ブランドイメージに優れ、Adobe Learning Managerに直接公開できるコースを作成します。

**主なハイライト**

- **AIガイド付きコースの作成** ：会話型AIは、トレーニングの目標を明確で測定可能な学習目標に変えるために、対象を絞った質問を行います。
- **文書に基づく生成**：作成者は、既存の文書、ポリシー、またはデッキをアップロードします。 AIは、そのマテリアルから概要を生成します。作成者は、何かが構築される前に、承認または編集します。
- **インストラクショナルサウンド出力** ：コース、評価、メディアは、構造化された学習原則を使用して生成されます。生成が速いだけでなく、教育的に効果的な出力が得られます。
- **Adobe Learning Managerへの直接公開** ：完成したコースは、Adobe Learning Managerに直接公開されます。個別のオーサリングツールや手動のSCORM書き出しはありません。
- **単一システムのワークフロー**:コースの作成、学習者の管理、レポート作成は1つのプラットフォームで行われるため、複数のオーサリングツールや配信ツールを管理するオーバーヘッドが解消されます。

## ログインする前に

>[!IMPORTANT]
>
>有効なAdobe Creative Cloudアカウントでログインする必要があります。 アカウントをお持ちでない場合は、Adobe Expressで無料アカウントを作成できます。 詳しくは、[無料のAdobe Expressアカウントを作成する](https://helpx.adobe.com/jp/express/web/adobe-express-subscription/free.html)をご覧ください。 Adobe認証情報を作成したら、Content Composerを起動し、ログインしてコースの作成を開始します。 組織内で既にCreative Cloudサブスクリプションを使用している場合は、Content Composerにログインする前に、管理者に連絡して、Creative Cloudアカウントをプロビジョニングしてもらってください。

>[!NOTE]
>
>コンテンツコンポーザーで最適なエクスペリエンスを実現するために、Google Chromeの使用をお勧めします。 FirefoxとSafariでは、機能や動作が異なる場合があります。

## コンテンツコンポーザーを試す

最初のコースを作成する準備はできましたか？ コンテンツコンポーザーを開き、プレーンランゲージのプロンプトからパブリッシュ対応コースにすばやく移行できます。

**[コンテンツコンポーザーを試す→](https://contentcomposer.adobe.io/)**

<!--
[![Open Content Composer](/assets/CTA.png)](https://contentcomposer-dev.adobe.io/)
-->

<!--[![Open Content Composer](../assets/CTA.png)](https://contentcomposer.adobe.io/)-->

## 概要 {#overview}

<table style="table-layout:auto; border:none; border-collapse:collapse;">
 <tbody>
  <tr>
   <td style="border:none;">
    <a href="what-is-content-composer.md">
    <img alt="コンテンツコンポーザーの基本を学ぶ" src="../assets/cc-get started.png" style="width:200px; height:120px; object-fit:cover;">
    </a>
    <div>
    <a href="what-is-content-composer.md"><strong>コンテンツコンポーザーの使い方</strong></a>
    </div>
    <p>コンテンツコンポーザーとは何か、コンテンツコンポーザーとは何か、コンテンツコンポーザーを開始する前に必要なコンテンツは何か。</p>
   </td>
   <td style="border:none;">
    <a href="write-a-prompt.md">
    <img alt="コースの作成" src="../assets/cc-create-course.png" style="width:200px; height:120px; object-fit:cover;">
    </a>
    <div>
    <a href="write-a-prompt.md"><strong>コースの作成</strong></a>
    </div>
    <p>単一のガイド付きワークフローで、単純な言語プロンプトからパブリッシュ対応コースに移行します。</p>
   </td>
   <td style="border:none;">
    <a href="general-course-settings.md">
    <img alt="コース設定の構成" src="../assets/cc-course-settings.png" style="width:200px; height:120px; object-fit:cover;">
    </a>
    <div>
    <a href="general-course-settings.md"><strong>コース設定の構成</strong></a>
    </div>
    <p>公開する前に、完了条件、クイズの採点、Adobe Learning Managerへの接続を設定します。</p>
   </td>
  </tr>
  <tr>
   <td style="border:none;">
    <a href="apply-theme.md">
    <img alt="コーステーマの管理" src="../assets/cc-branding.png" style="width:200px; height:120px; object-fit:cover;">
    </a>
    <div>
    <a href="apply-theme.md"><strong>コーステーマの管理</strong></a>
    </div>
    <p>ビジュアルテーマを適用、カスタマイズ、作成、読み込みすることで、コースの外観と印象を制御します。</p>
   </td>
   <td style="border:none;">
    <a href="share-collaborate.md">
    <img alt="共有と共同作業" src="../assets/cc-share.png" style="width:200px; height:120px; object-fit:cover;">
    </a>
    <div>
    <a href="share-collaborate.md"><strong>共有と共同作業</strong></a>
    </div>
    <p>レビュー用のコースを同僚と共有するか、学習者がコースに直接アクセスできるようにします。</p>
   </td>
   <td style="border:none;">
    <a href="publish-to-alm.md">
    <img alt="Adobe Learning Manager に公開" src="../assets/cc-publish-alm.png" style="width:200px; height:120px; object-fit:cover;">
    </a>
    <div>
    <a href="publish-to-alm.md"><strong>PublishからAdobe Learning Managerへ</strong></a>
    </div>
    <p>完成したコースをAdobe Learning Managerに導入し、Content ComposerとALMによってオーサリング、配信、レポートの各責任がどのように分担されているかを理解します。</p>
   </td>
  </tr>
  </tbody>
</table>

## 項目を調べる {#lookthingsup}

クイックアンサー、現在の制約、および完全なJSONスキーマ。 素早く何かを調べるのに必要なものがすべて。

<table style="table-layout:auto; border-collapse:collapse;" border="1" bordercolor="transparent" cellpadding="0" cellspacing="0">
 <tbody>
  <tr>
   <td style="border:1px solid transparent;">
    <a href="content-composer-beta-limitations.md">
    <img alt="ベータ版の制限" src="../assets/cc-limitations.png" style="width:200px; height:120px; object-fit:cover;">
    </a>
    <div>
    <a href="content-composer-beta-limitations.md"><strong>ベータ版の制限</strong></a>
    </div>
    <p>現在の制約、回避策およびロードマップのステータスの完全なリスト。 機能の出荷時に更新されます。</p>
   </td>
   <td style="border:1px solid transparent;">
    <a href="content-composer-faq.md">
    <img alt="Content ComposerのFAQ" src="../assets/cc-faq.png" style="width:200px; height:120px; object-fit:cover;">
    </a>
    <div>
    <a href="content-composer-faq.md"><strong>コンテンツコンポーザーに関するFAQ</strong></a>
    </div>
    <p>オーサリング、設定、共有、公開に関するよくある質問とその回答をご覧ください。</p>
   </td>
   <td style="border:1px solid transparent;">
    <a href="theme-json-reference.md">
    <img alt="Theme JSONプロパティリファレンス" src="../assets/cc-theme-ref.png" style="width:200px; height:120px; object-fit:cover;">
    </a>
    <div>
    <a href="theme-json-reference.md"><strong>テーマのJSONプロパティの参照</strong></a>
    </div>
    <p>Content ComposerテーマのJSONスキーマのすべてのプロパティ。説明とサンプル値が含まれています。</p>
   </td>
  </tr>
 </tbody>
</table>

## 作成を開始 {#startcreating}

必要なものがすべて揃っています。 コンテンツコンポーザーを開き、最初のコースを作成します。

[**コンテンツコンポーザーを試す**](https://contentcomposer.adobe.io/)
