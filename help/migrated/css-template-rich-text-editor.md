---
jcr-language: en_us
title: リッチテキストエディターのCSSテンプレート
description: リッチテキストエディターのCSSテンプレート
contentowner: saghosh
preview: true
source-git-commit: 9325abb9cda8c8a019c9d72c1944a8284f38f83e
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 70%

---



# リッチテキストエディターのCSSテンプレート

## CSS が必要な理由

リッチテキストは、HTML マークアップで構成されています。 マークアップをそのままレンダリングすると、ブラウザーにデフォルトのスタイルが適用されます。 その場合、企業のスタイルガイドラインに適合しなくなる可能性があります。 ガイドラインに適合するには、CSS が必要です。

## デフォルトのスタイル

添付された CSS のスタイルシートには、Learning Manager で適用されるスタイルが含まれています。このスタイルは、さまざまユースケースを念頭において調整されています。 自分の命名規則やビルドシステムに沿って、添付された CSS ファイルをダウンロードして Web アプリに読み込みます。 定義されたCSSクラスはql-editorクラスの名前空間に属し、既存のスタイルと干渉しません。

## スタイルのカスタマイズ

デフォルトのスタイルは万能ではありません。 指定された CSS を上書きすることで、カスタマイズできます。 すべてのスタイルは、改良版のセレクターとして「ql-editor」に囲まれます。 次のクラスが使用されます。

* **インデント**: li.ql-indent-$number。 $number には、1～9 が入ります。
* **サイズ**: ql-size-small、ql-size-large、ql-size-huge
* **整列**: ql-align-center、ql-align-justify、ql-align-right
* **color**: ql-color-$color。 $color に入る色：white、red、orange、yellow、green、blue、purple
* **背景**: ql-bg-$color。 $color に入る色：black、red、orange、yellow、green、blue、purple
* **htmlタグ**: p、ol、ul、pre、blockquote、h1、h2、h3、h4、h5、h6

[CSS ファイルをカスタマイズに使用できます。](assets/ql-headless.css)
