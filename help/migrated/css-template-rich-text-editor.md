---
jcr-language: en_us
title: リッチテキストエディターのCSSテンプレート
description: リッチテキストエディターのCSSテンプレート
contentowner: saghosh
preview: true
product_v2:
  - id: ed12e5b7-96e3-45e7-a17f-de222065ebcb
    internal-label: Learning Manager
source-git-commit: c061ccbefe8d40154220587796062d335e35de77
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 72%
---


# リッチテキストエディターのCSSテンプレート

## CSS が必要な理由

リッチテキストは、HTML マークアップで構成されています。 マークアップをそのままレンダリングすると、ブラウザーにデフォルトのスタイルが適用されます。 その場合、企業のスタイルガイドラインに適合しなくなる可能性があります。 ガイドラインに適合するには、CSS が必要です。

## デフォルトのスタイル

添付された CSS のスタイルシートには、Learning Manager で適用されるスタイルが含まれています。 このスタイルは、さまざまユースケースを念頭において調整されています。 自分の命名規則やビルドシステムに沿って、添付された CSS ファイルをダウンロードして Web アプリに読み込みます。 定義された CSS クラスは、「ql-editor」クラスの名前空間に属し、既存のスタイルに干渉することはありません。

## スタイルのカスタマイズ

デフォルトのスタイルは万能ではありません。 指定された CSS を上書きすることで、カスタマイズできます。 すべてのスタイルは、改良版のセレクターとして「ql-editor」に囲まれます。 次のクラスが使用されます。

* **インデント**: li.ql-indent-$number。 $number には、1～9 が入ります。
* **サイズ**: ql-size-small、ql-size-large、ql-size-huge
* **アラインメント**: ql-align-center、ql-align-justify、ql-align-right
* **color**: ql-color-$color。 $color に入る色：white、red、orange、yellow、green、blue、purple
* **背景**: ql-bg-$color。 $color に入る色：black、red、orange、yellow、green、blue、purple
* **htmlタグ**: p、ol、ul、pre、blockquote、h1、h2、h3、h4、h5、h6

[CSS ファイルをカスタマイズに使用できます。](assets/ql-headless.css)
