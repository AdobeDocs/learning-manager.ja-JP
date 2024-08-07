---
description: Learning Manager でのユーザーデータの消去について
jcr-language: en_us
title: ユーザーを消去
contentowner: dvenkate
exl-id: 4449146c-6247-44fb-b695-a12023c31dc6
source-git-commit: 890775dafffd3b9d717c39507490977f51f163d4
workflow-type: tm+mt
source-wordcount: '853'
ht-degree: 75%

---

# ユーザーを消去

Learning Manager でのユーザーデータの消去について

## 概要 {#overview}

ユーザーを特定できる個人情報や学習記録を Learning Manager から削除する場合、ユーザーの消去機能を使用します。「ユーザーを削除」と「ユーザーを消去」は別個の機能です。 削除したユーザーは復元できますが、ユーザーを消去した場合、そのユーザーに関連付けられたすべてのユーザーデータと学習記録が消去されるため、復元できません。

ユーザーの消去を実行した場合：

* ユーザーを消去した場合、読み込みログのリンクは機能せず、古いCSVのダウンロードと、ユーザーデータのシステムへの再取り込みが回避されます。
* 作成者を消去すると、作成者の名前は、そのユーザーを消去した管理者の名前に置き換えられます。
* インストラクタを消去すると、セッションに表示されなくなります。 このようなセッションでは、管理者がインストラクターを変更または追加する必要があります。
* Learning Manager でユーザーを消去しても、外部アプリケーション（サードパーティ製のシステムや自分で作成した他のアプリケーション）ではユーザーを削除できません。そのようなアプリケーションからユーザーを削除してもらうには、外部アプリケーションのオーナーに連絡してください。
* 消去されたユーザーをコネクタの構成設定で参照すると、そのコネクタは無効になります。 再開するには、管理者がコネクタを再構成する必要があります。

<!---### Manage users

In this training, you will learn how to assign and remove roles, send a welcome email, and delete and purge users. 

[![button](assets/launch-training-button.png)](https://learningmanager.adobe.com/app/learner?accountId=98632&sdid=4X3B8VJ2&mv=display&mv2=display#/course/7555586)

If you're unable to launch the training, write to <almacademy@adobe.com>.-->

## ユーザーを消去する方法

ユーザーを消去するには、次の手順に従います。

1. 管理者として、左側のペインから「**[!UICONTROL ユーザー]**」を選択します。 **[!UICONTROL 社内ユーザー]**&#x200B;ページが開きます。
1. 消去したいユーザーを削除します。 チェックボックスを使用して、削除するユーザーを選択します。一度に複数のユーザーを選択することも可能です。 「**[!UICONTROL アクション]**」ドロップダウンを開き、「**[!UICONTROL ユーザーを削除]**」を選択します。
1. 左側のペインで、「**[!UICONTROL ユーザークリーンアップ]**」を選択します。 **[!UICONTROL ユーザークリーンアップ]**&#x200B;ページが表示され、削除されたユーザーのリストが表示されます。 ラジオボタンを使用して、消去するユーザーを選択します。 一度に消去できるユーザーは 1 人だけです。

   ![](assets/purge-1.png)

   *消去するユーザーを選択してください*

1. **[!UICONTROL アクション]**&#x200B;ドロップダウンメニューを開き、「**[!UICONTROL ユーザーを消去]**」を選択します。

   ![](assets/purge-2.png)

   *[ユーザーの消去]オプションを選択する*

1. 確認のためのダイアログボックスが表示されます。 一度消去すると、選択したユーザーに関連付けられたすべてのユーザーデータと学習レコードは永久的に削除され、 操作を元に戻すことはできません。 確認するには、[**[!UICONTROL 消去]**]をクリックします。

   ![](assets/purge-3.png)

   *ユーザーを削除した後の確認メッセージ*

1. 確認して「消去」をクリックすると、消去リクエストが承認されます。 操作が完了すると、通知が届きます。 また、消去リクエスト ID が送られます。 この ID を CSM に提供すると、リクエストを追跡できます。

## ユーザーの一括消去

最初の 50 人のユーザーを選択し、そのユーザーをまとめて消去できます。 これにより管理者は一度に 50 人のユーザーを選択して、まとめて消去できるようになります。 この機能は、管理者がユーザーを一括消去する場合に役立ちます。 消去対象として選択されているユーザーを必ず確認することをお勧めします。 対象のユーザーのみが消去されるようにするには、この確認が重要です。

![](assets/bulk-purge-users.png)

*ユーザーを一括消去*

+++ユーザーの消去アクションの結果について読む

<table>
 <tbody>
  <tr>
   <th><strong>Learning Manager UI- Enterprise を使用した消去</strong></th>
   <th> </th>
  </tr>
  <tr>
   <td>リクエスト中のエンタープライズ版アカウントから選択したユーザーを削除する。<br></td>
   <td>可</td>
  </tr>
  <tr>
   <td>選択したユーザー電子メールと adobe_id 電子メールが一致するすべての体験版アカウントから、ユーザーを全員削除する。</td>
   <td>可</td>
  </tr>
  <tr>
   <td>選択したユーザー電子メールと adobe_id 電子メールが一致するすべての体験版アカウントから、ユーザーを全員削除する。体験版アカウントの作成者も削除する。</td>
   <td>不可</td>
  </tr>
  <tr>
   <td>リクエスト中のエンタープライズ版アカウントとすべての体験版アカウントの他のすべてのフィールドから、ユーザーの電子メールを削除する。</td>
   <td>可</td>
  </tr>
  <tr>
   <td>削除確認のイニシエータに通知する。</td>
   <td>可</td>
  </tr>
  <tr>
   <td><strong>Learning Manager UI- Non-Enterpriseを使用した消去</strong></td>
   <td> </td>
  </tr>
  <tr>
   <td>リクエスト中の体験版アカウントから選択したユーザーを削除する。</td>
   <td>可</td>
  </tr>
  <tr>
   <td>選択したユーザー電子メールと adobe_id 電子メールが一致するすべての体験版アカウントから、ユーザーを全員削除する。</td>
   <td>可</td>
  </tr>
  <tr>
   <td>選択したユーザー電子メールと adobe_id 電子メールが一致するすべての体験版アカウントから、ユーザーを全員削除する。体験版アカウントの作成者も削除する。</td>
   <td>不可</td>
  </tr>
  <tr>
   <td>すべての体験版アカウントの他のすべてのフィールドからユーザーの電子メールを削除する。</td>
   <td>可</td>
  </tr>
  <tr>
   <td>削除確認のイニシエータに通知する。</td>
   <td>可</td>
  </tr>
  <tr>
   <td><strong>他のユーザーを消去する – Enterprise（社内ユーザーまたは外部のLearning Managerユーザーでない場合）</strong></td>
   <td> </td>
  </tr>
  <tr>
   <td>リクエスト中のエンタープライズ版アカウントとすべての体験版アカウントの他のすべてのフィールドから、選択したユーザーを削除する。</td>
   <td>可</td>
  </tr>
  <tr>
   <td>アカウントからのユーザーの削除。</td>
   <td>不可</td>
  </tr>
  <tr>
   <td>削除確認のイニシエータに通知する。 </td>
   <td>可</td>
  </tr>
  <tr>
   <td><strong>消去</strong> <strong>その他のユーザー – Enterprise以外のユーザー（社内ユーザーまたは外部のLearning Managerユーザーでない場合）</strong></td>
   <td> </td>
  </tr>
  <tr>
   <td>すべての体験版アカウントの他のすべてのフィールドから選択したユーザーを削除する。</td>
   <td>可</td>
  </tr>
  <tr>
   <td>アカウントからのユーザーの削除。</td>
   <td>不可</td>
  </tr>
  <tr>
   <td>削除確認のイニシエータに通知する。</td>
   <td>可</td>
  </tr>
  <tr>
   <td><strong>Adobe IMS- Enterprise を使用した消去</strong></td>
   <td> </td>
  </tr>
  <tr>
   <td>リクエストについてエンタープライズ版の管理者に通知する。</td>
   <td>可</td>
  </tr>
  <tr>
   <td>通知を送信する場合に、電子メールフィールドを確認する。</td>
   <td>不可</td>
  </tr>
  <tr>
   <td><strong>Adobe IMS- Non-Enterprise を使用した消去</strong></td>
   <td> </td>
  </tr>
  <tr>
   <td>提供された AdobeID/電子メールを持つユーザー全員を、すべての体験版アカウントから削除する。</td>
   <td>可</td>
  </tr>
  <tr>
   <td>提供された電子メール/Adobe ID がアカウントの作成者である場合に、体験版アカウントのユーザーを全員削除する。</td>
   <td>可</td>
  </tr>
  <tr>
   <td>すべての体験版アカウントの他のすべてのフィールドから選択した電子メールIDを削除する。</td>
   <td>可</td>
  </tr>
 </tbody>
</table>

+++

Learning ManagerはGDPRに準拠しました。 GDPR準拠に関する詳細については、[Learning ManagerのGDPR準拠](../../kb/prime-gdpr.md)を参照してください。

## よくある質問 {#frequentlyaskedquestions}

+++消去リクエストが完了するまでに何日かかりますか？

ユーザーの消去リクエストが完了するまでには、最大30日かかります。
+++

+++Learning Managerで一括消去を実行できますか？

はい、一括消去を実行できます。ただし、一括消去を実行できるのは 50 ユーザーまでです。
+++
