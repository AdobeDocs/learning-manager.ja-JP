---
title: Safe Exam Browser
description: Adobe Learning ManagerのアカウントレベルでSafe Exam Browserとの連携を有効にすると、作成者がネイティブクイズに安全なブラウザー環境を要求できるようになります。
source-git-commit: 38dba6765ff013e446ab1f6098e9f1df0c24d0f9
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 1%
---

# Safe Exam Browser

Safe Exam Browserは、評価時に他のブラウザーやアプリケーションへのアクセスを制限することで、Adobe Learning Managerのネイティブなクイズを学習者が安全に受けられる環境を提供します。

管理者は、アカウントレベルで安全試験ブラウザー統合を有効にし、設定ファイル(.seb)をアップロードしてクイズ制限を定義できます。 統合を有効にすると、作成者は個々のクイズを設定して、安全試験ブラウザーの使用を必要とすることができます。

この記事では、アカウントでSafe Exam Browser統合を有効にする方法について説明します。

## 安全な試験ブラウザー統合を有効にする

作成者がクイズを設定するときにオプションを使用できるようにするには、「安全試験ブラウザー」統合を有効にします。 始める前に、お使いのアカウントに対応するSafe Exam Browserファイルがあることを確認します。

Safe Exam Browserの統合を有効にするには：

1. ALMに&#x200B;**管理者**&#x200B;としてログインします。
1. **設定** > **一般**&#x200B;を選択します。
1. **Safe Exam Browser統合**&#x200B;に移動します。
1. 「**編集**」を選択します。

   これにより、**Safe Exam Browser統合**&#x200B;が拡張されます。

1. 「**有効にする**」を選択します。
1. 「**参照**」を選択し、システムからSafe Exam Browserファイルをアップロードします。 詳細については、[安全な試験ブラウザーファイルを構成する](#configure-the-seb-file-for-macos)構成を参照してください。

   ![全般の設定での安全な試験ブラウザーの統合設定](assets/safe-exam-browser-integration-settings.png "全般の設定での安全な試験ブラウザーの統合設定")

1. 「**保存**」を選択します。

   サポートされているクイズを設定するときに、作成者がセーフ試験ブラウザーを使用して有効にできるようになりました。

### macOS用の.sebファイルの設定 {#configure-the-seb-file-for-macos}

SEB構成ツールを使用して.sebファイルを作成し、クイズ制限、セキュリティ設定、および許可されるアプリケーションを定義します。 Safe Exam Browser(SEB)を使用する前に、.sebファイルが次の要件を満たしていることを確認してください。

1. browserWindowWebViewパラメーターを3 (整数)に設定して、SEBを有効にします。
1. startURLに、ターゲット環境に対応するURLを設定します。
1. .sebファイルに必要なquitURL情報が含まれていることを確認します。
