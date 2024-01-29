---
jcr-language: en_us
title: リッチテキストエディターのCSSテンプレート
description: リッチテキストエディターのCSSテンプレート
contentowner: saghosh
preview: true
source-git-commit: 9325abb9cda8c8a019c9d72c1944a8284f38f83e
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---



# リッチテキストエディターのCSSテンプレート

## CSSが必要な理由

リッチテキストは、HTMLマークアップで構成されています。 マークアップをそのままレンダリングすると、ブラウザーによってデフォルトのスタイルが適用されます。 これは多くの場合、会社のスタイルガイドラインとうまくいきません。 ガイドラインを満たすにはCSSが必要です。

## デフォルトのスタイル

添付されたCSSのスタイルシートには、Learning Managerで適用されるスタイルが含まれています。 このスタイルは、ほとんどのユースケースを考慮して調整されています。 命名規則やビルドシステムに従って、添付されたCSSファイルをダウンロードして、webアプリに読み込みます。 定義されたCSSクラスはql-editorクラスの名前空間に属し、既存のスタイルと干渉しません。

## スタイルのカスタマイズ

デフォルトのスタイルは、すべてのユーザーのニーズを満たしているとは限りません。 指定されたCSSを上書きすることで、カスタマイズできます。 すべてのスタイルは、子孫セレクターとしてql-editorに囲まれます。 次のクラスが使用されます。

* **インデント**: li.ql-indent-$number. $numberには1 ～ 9の値を指定できます。
* **サイズ**: ql-size-small、ql-size-large、ql-size-huge
* **整列**: ql-align-center、ql-align-justify、ql-align-right
* **カラー**: ql-color-$color。 $color =白、赤、オレンジ、黄、緑、青、紫
* **背景**: ql-bg-$color。 $color = black、red、orange、yellow、green、blue、purple
* **htmlタグ**:p、ol、ul、pre、blockquote、h1、h2、h3、h4、h5、h6

[カスタマイズに使用するCSSファイル。](assets/ql-headless.css)
