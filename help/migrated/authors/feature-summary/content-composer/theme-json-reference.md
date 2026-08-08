---
description: Content ComposerテーマのJSONスキーマに含まれるすべてのプロパティの完全な参照です。これには、パレットトークン、フォントスタック、半径および間隔トークン、テキストロールの値、コンポーネントプロパティ、評価スタイルが含まれます。
jcr-language: en_us
title: Adobe Learning Manager Content ComposerテーマJSONプロパティリファレンス
source-git-commit: ea6d296fa99686136ab08d756a20570a4681d704
workflow-type: tm+mt
source-wordcount: '1899'
ht-degree: 5%

---


# Adobe Learning Manager Content ComposerテーマJSONプロパティリファレンス

Content ComposerテーマJSONファイルの各プロパティの完全なリファレンス。説明とサンプル値を含みます。

テーマを識別および説明する最上位レベルのフィールド。

## **メタデータ**

| **プロパティ** | **タイプ** | **説明** | **スレート値** |
|--------------|----------|----------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------|
| id | string | 一意のテーマ識別子です。 小文字、ハイフンのみ。スペースや特殊文字は使用できません。 テーマを参照するために内部的に使用されます。 | 「スレート」 |
| 名前 | string | コーステーマパネルに表示される表示名。 | 「スレート」 |
| バージョン | string | セマンティックバージョン番号。 新しいテーマには「1.0.0」を使用します。 | &quot;1.0.0&quot; |
| 説明 | string | テーマの視覚的特徴の簡単な説明。 | 「クリーム色の背景、Adobeレッドのアクセント、Roboto Slab + Roboto type systemを備えた、温かみのある権威あるテーマ」 |
| author | string | テーマ作成者またはチームの名前。 | 「コンテンツコンポーザー」 |
| source | string | テーマの原点。 組み込みのテーマの「出荷済み」。 ユーザーが作成したテーマの「カスタム」 | &quot;カスタム&quot; |
| isDefault | ブール値 | このテーマを新しいコースに自動的に適用するかどうかを指定します。 ほとんどの場合、 falseに設定します。 | false |

## **foundation.palette**

テーマのカラーの基礎を形成する7つのコアカラートークン。 すべてのエレメント値は、16進数値をハードコードするのではなく、var(—tokenName)を使用してこれらのトークンを参照します。

| **プロパティ** | **タイプ** | **説明** | **スレート値** |
|------------------|------------|---------------------------------------------------------------------------------------------------------------------------|-----------------|
| foreground | 16進数カラー | 背景に配置するテキスト、アイコン、UI要素のプライマリ描画色。 | #1A1A1A |
| 背景 | 16進数カラー | メインコースカンバスとスライドの背景色。 | #FAF7F2 |
| アクセント | 16進数カラー | ボタン、選択したステート、進行状況インジケーター、レッスンヘッダー、インタラクティブハイライトに適用されたブランドアクセントの色。 | #E8001C |
| backgroundSubtle | 16進数カラー | カード、パネル、ナビゲーション、およびコンポーネントの塗りつぶしのセカンダリ背景色。 | #F0EBE1 |
| 二次 | 16進数カラー | 境界線、境界線、非アクティブなUI要素の色。 | #D9D3C9 |
| textPrimary | 16進数カラー | すべての見出しと本文のコンテンツのプライマリテキストカラー。 | #1A1A1A |
| textInverse | 16進数カラー | アクセントカラーのボタンラベルなど、濃い色またはアクセントカラーの背景に配置されたコンテンツのテキストカラー。 | #FFFFFF |

## **foundation.fonts**

テーマ内のすべてのテキストの役割に適用される2つのフォントスタック。 var(—font-heading)またはvar(—font-body)を使用して、エレメント値を参照します。

| **プロパティ** | **タイプ** | **説明** | **スレート値** |
|--------------|-------------------|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------|
| 見出し | フォントスタック文字列 | レッスンのタイトル、トピックタイトル、見出し表示のフォントファミリー。 Webに適したフォールバックを含めます。 | 「Roboto Slab, Georgia, &#39;Times New Roman&#39;, serif」 |
| body | フォントスタック文字列 | 段落テキスト、キャプション、クイズ質問、UIラベルのフォントファミリー。 Webに適したフォールバックを含めます。 | 「Roboto, -apple-system, BlinkMacSystemFont, &#39;Segoe UI&#39;, sans-serif」 |

## **foundation.spacing**

ベースラインとして使用する水平方向および垂直方向の間隔トークン。 これらのコンポーネントは、horizontalSpacingScaleおよびverticalSpacingScale乗数を使用して拡大・縮小されます。

| **パス** | **タイプ** | **説明** | **スレート値** |
|---------------|----------|-------------------------------------|-----------------|
| horizontal.xs | px値 | 水平方向の最小間隔単位 | 4px |
| horizontal.s | px値 | 水平方向の間隔（小）の単位 | 8px |
| horizontal.m | px値 | 水平方向の中間隔の単位 | 12px |
| horizontal.l | px値 | 水平方向の間隔の大きい単位 | 16px |
| horizontal.xl | px値 | 特大の水平方向の間隔単位 | 24px |
| vertical.xs | px値 | 縦方向の最小間隔単位 | 4px |
| 垂直方向.s | px値 | 縦方向の間隔の小さい単位 | 8px |
| vertical.m | px値 | 垂直方向間隔単位（中） | 16px |
| 垂直方向.l | px値 | 行間の大きい単位 | 24px |
| vertical.xl | px値 | 特大の縦方向の間隔単位 | 32px |

## **foundation.radius**

コンポーネントとカードの角の丸みを制御する境界線半径トークン。

| **プロパティ** | **タイプ** | **説明** | **スレート値** |
|--------------|----------|---------------------------------------------------------|-----------------|
| なし | px値 | 丸みなし – 鋭角。 常に「0px」。 | 0px |
| s | px値 | コーナーの丸みを少し調整するための小さな半径です。 | 4px |
| m | px値 | 標準カードとコンポーネントの丸めの半径（中）。 | 8px |
| l | px値 | 突出した丸みの半径（大）。 | 16px |
| フル | px値 | 丸薬または円のシェイプ全体。 常に&quot;9999px&quot;. | 9999px |

## **foundation.logo**

| **プロパティ** | **タイプ** | **説明** | **スレート値** |
|--------------|----------------|----------------------------------------------------------------------------------------------|-----------------|
| ロゴ | stringまたはnull | コースヘッダーに表示されるロゴ画像のURLまたはファイルパス。 ロゴがない場合はnullに設定します。 | null |

## **elements.text**

コース内の各テキストロールのタイポグラフィプロパティ。 すべての役割は、同じプロパティのセットを共有します。

### **テキストロール**

| **ロール** | **適用先** |
|--------------|------------------------------------------------------------------------------|
| lessonTitle | レッスンの最初のスライドのメインタイトル |
| topicTitle | 各トピックスライドの上部にある見出し |
| blockHeading | アコーディオンヘッダーやカードタイトルなどのコンテンツコンポーネント内の見出し |
| 小見出し | トピックスライド内のセカンダリ見出し |
| 質問別に | クイズとナレッジチェックの質問テキスト |
| 表題 | 画像とメディアブロックの下のキャプション |
| 段落 | コンテンツスライドの本文 |
| buttonLabel | ボタンおよび行動喚起エレメントのテキスト |

### **共有テキストプロパティ**

次のプロパティは、上記のすべてのテキストロールに適用されます。

| **プロパティ** | **タイプ** | **承認された値** | **説明** |
|--------------------|-----------------------|--------------------------------------------------------------------|---------------------------------------------------------|
| fontFamily | CSS変数またはフォントスタック | var(—font-heading)、var(—font-body)、またはフォントスタック文字列全体 | このテキストロールのフォントファミリ。 |
| fontSize | px値 | 任意のピクセル値 | フォントサイズ： |
| fontWeight | string | 「太字」または「標準」のみ：数値はサポートされていません | フォントの太さ： |
| fontStyle | string | &quot;normal&quot;または&quot;italic&quot; | フォントスタイル： |
| カラー | CSSのvarまたはhex | var(—tokenName)または直接の16進数値を介したパレットトークン | テキストカラー： |
| textAlign | string | &quot;left&quot;、&quot;center&quot;、または&quot;right&quot; | テキストの水平方向の整列。 |
| letterSpacing | string | &quot;normal&quot;、px値、またはem値 | 文字と文字の間隔 |
| lineHeight | string | パーセントまたは単位のない値 | 線のHeight。 |
| textDecoration | string | &quot;none&quot;、&quot;underline&quot;、または&quot;line-through&quot; | テキストの装飾： |
| textTransform | string | &quot;none&quot;、&quot;uppercase&quot;、&quot;lowercase&quot;または&quot;capitalize&quot; | テキストの大文字と小文字の変換。 |
| paddingInlineStart | px値 | 任意のピクセル値 | テキストブロックに適用された左パディング |
| paragraphSpacing | px値 | 任意のピクセル値 | テキストブロック内で各段落の下に追加される間隔。 |

### **テキストロールの値 – スレートテーマ**

| **ロール** | **fontFamily** | **fontSize** | **fontWeight** | **fontStyle** | **色** | **textAlign** | **文字間隔** | **lineHeight** | **textTransform** |
|--------------|---------------------|--------------|----------------|---------------|--------------------|---------------|-------------------|----------------|-------------------|
| lessonTitle | var(—font-heading) | 48px | bold | normal | var(—textPrimary) | 中央 | -0.01em | 130% | なし |
| topicTitle | var(—font-heading) | 40px | normal | normal | var(—textPrimary) | 左 | 0 | 135% | なし |
| blockHeading | var(—font-heading) | 24px | bold | normal | var(—textPrimary) | 左 | 0 | 140% | なし |
| 小見出し | var(—font-body) | 20px | bold | normal | var(—textPrimary) | 左 | 0.01em | 150% | なし |
| 質問別に | var(—font-heading) | 24px | normal | normal | var(—textPrimary) | 左 | 0 | 150% | なし |
| 表題 | var(—font-body) | 13px | normal | normal | var(—textPrimary) | 左 | 0.02em | 170% | なし |
| 段落 | var(—font-body) | 16px | normal | normal | var(—textPrimary) | 左 | 0.01em | 190% | なし |
| buttonLabel | var(—font-body) | 14px | bold | normal | var(—textInverse) | 中央 | 0.06em | 125% | 大文字 |

## **要素 – 構造面**

コースの固定レイアウト表面の背景と境界線を制御するプロパティ。

| **要素** | **プロパティ** | **タイプ** | **説明** | **スレート値** |
|--------------|--------------|-------------------|---------------------------------------------------|----------------------------|
| カンバス | 背景 | CSS変数 | メインコースカンバスの背景色 | var(—background) |
| header | 背景 | CSS変数 | コースヘッダーバーの背景色 | var(—background) |
| header | 境界線 | CSS境界文字列 | コースヘッダーバーの下部の境界 | 1px solid var（ – セカンダリ） |
| footer | 背景 | CSS変数 | コースフッターバーの背景色 | var(—background) |
| footer | 境界線 | CSS境界文字列 | コースフッターバーの上の境界 | 1px solid var（ – セカンダリ） |
| lessonHeader | 背景 | CSS変数 | レッスンタイトルのヘッダー領域の背景色 | var(—accent) |
| topic | 背景 | CSS変数 | 各トピックスライドの背景色 | var(—background) |
| topic | 境界線 | CSS境界文字列 | トピックのスライドコンテナの境界線 | 1px solid var（ – セカンダリ） |
| 航法 | 背景 | CSS変数 | レッスンナビゲーションパネルの背景色 | var(—backgroundSubtle) |
| 航法 | 境界線 | CSS境界文字列 | レッスンナビゲーションパネルの境界 | 1px solid var（ – セカンダリ） |
| ボタン | 背景 | CSS変数 | プライマリアクションボタンの背景色 | var(—accent) |
| ページ設定 | 背景 | CSS変数 | ページコントロールの背景色 | var(—backgroundSubtle) |

## **要素 – 共有コンポーネントのプロパティ**

paragraphBlock、videoBlock、imageGrid、accordion、carousel、flipCard、timelineなどのプロパティが、すべてのコンテンツブロックコンポーネントに表示されます。

| **プロパティ** | **タイプ** | **説明** |
|------------------------|-------------------|---------------------------------------------------------------------------------------------------|
| 背景 | CSSの変数またはカラー | コンポーネントブロックの外側の背景。 通常は「透明」。 |
| cardBackgroundColor | CSSの変数またはカラー | コンポーネント内の個々のカードの背景塗りつぶし。 |
| cardBorder | CSS境界文字列 | 各カードに適用される境界線。 完全なCSSの略語(例：&quot;1px solid var(—secondary)&quot;)。 |
| cardShadowOffset | string | カードドロップシャドウのXおよびYオフセット（例：「0px 2px 6px」）。 |
| cardShadowColor | CSSの変数またはカラー | カードのドロップシャドウの色。 |
| cardShadowOpacity | パーセント文字列 | カードドロップシャドウの不透明度。 「0%」に設定すると、シャドウが削除されます。 |
| horizontalSpacingScale | 数値文字列 | このコンポーネントの水平方向の間隔トークンに適用される乗数。 「1」はデフォルトの間隔を使用します。 |
| verticalSpacingScale | 数値文字列 | このコンポーネントの垂直間隔トークンに適用される乗数。 「1」はデフォルトの間隔を使用します。 |
| radiusScale | 数値文字列 | このコンポーネントの半径トークンに適用される乗数。 「1」はデフォルトの半径を使用します。 |
| nestedAccentColor | CSSの変数またはカラー | コンポーネント内の入れ子になった要素のアクセント色です。 paragraphBlockにのみ適用されます。 |

### **共有コンポーネントの値 – スレートテーマ**

| **コンポーネント** | **cardBackgroundColor** | **cardBorder** | **cardShadowOpacity** |
|----------------|-----------------------------|----------------------------|---------------------------|
| paragraphBlock | var(—backgroundSubtle) | 1px solid var（ – セカンダリ） | 8% |
| videoBlock | var(—backgroundSubtle) | 1px solid var（ – セカンダリ） | 8% |
| imageGrid | var(—backgroundSubtle) | 1px solid var(—accent) | 8% |
| アコーディオン | var(—backgroundSubtle) | 1px solid var（ – セカンダリ） | 8% |
| カルーセル | var(—backgroundSubtle) | 1px solid var（ – セカンダリ） | 8% |
| flipCard | var(—backgroundSubtle) | 1px solid var（ – セカンダリ） | 8% |
| タイムライン | var(—backgroundSubtle) | 1px solid var（ – セカンダリ） | 8% |

## **要素 – コンポーネント固有のプロパティ**

個々のコンポーネントタイプに固有のプロパティ。

| **コンポーネント** | **プロパティ** | **タイプ** | **説明** | **スレート値** |
|----------------|--------------------------|----------|------------------------------------------------------------------|-------------------------|
| paragraphBlock | nestedAccentColor | CSS変数 | 段落ブロック内のネストされたエレメントのアクセントカラー | var(—accent) |
| flipCard | cardFrontBackgroundColor | CSS変数 | フリップカードの前面の背景色 | var(—backgroundSubtle) |
| flipCard | cardBackBackgroundColor | CSS変数 | フリップカードの裏面の背景色 – リビールカラー | var(—accent) |
| flipCard | arrowColor | CSS変数 | 反転インジケーターの矢印アイコンの色 | var(—textInverse) |
| タブ | activeBg | CSS変数 | 現在選択されているタブの背景色 | var(—accent) |
| タブ | inactiveBg | CSS変数 | 選択されていないタブの背景色 | var(—backgroundSubtle) |
| タブ | containerBg | CSS変数 | タブバーコンテナの背景色 | var(—backgroundSubtle) |
| タイムライン | trackColor | CSS変数 | タイムラインノード間の接続線のカラー | var(—secondary) |
| タイムライン | progressCompletedBg | CSS変数 | 完了したタイムライン進行状況マーカーの塗りつぶしの色 | var(—accent) |
| タイムライン | progressCurrentBorder | CSS変数 | 現在のタイムラインの進行状況マーカーの境界線の色 | var(—accent) |
| タイムライン | progressUnreachedBg | CSS変数 | タイムラインマーカーの塗りのカラーがまだ設定されていません | var(—secondary) |
| タイムライン | progressUnreachedBorder | CSS変数 | タイムラインマーカーの境界線のカラーがまだ到達していません | var(—backgroundSubtle) |

## **elements.assessment**

クイズおよびナレッジチェックコンポーネントのプロパティ。

| **プロパティ** | **タイプ** | **説明** | **スレート値** |
|----------------------------|----------------|------------------------------------------------------------------------------|-------------------------|
| 背景 | CSS変数 | 評価ブロックの外側の背景 | 透明 |
| optionTextColor | CSS変数 | 回答オプションラベルのテキストの色 | var(—textPrimary) |
| optionIndicatorColor | CSS変数 | ラジオボタンまたはチェックボックスインジケーターの色 | var(—accent) |
| optionSelectedColor | CSS変数 | 選択したオプションインジケーターに適用されるカラー | var(—accent) |
| optionCheckmarkColor | CSS変数 | 選択したオプションに表示されるチェックマークアイコンの色 | var(—textInverse) |
| optionBackgroundColor | CSS変数 | 各回答オプションの背景色 | var(—background) |
| optionHoverBackgroundColor | CSS変数 | カーソルを合わせたときに応答オプションの背景色 | var(—backgroundSubtle) |
| buttonBackgroundColor | CSS変数 | [送信]ボタンまたは[回答の確認]ボタンの背景色 | var(—accent) |
| buttonTextColor | CSS変数 | [送信]または[応答の確認]ボタンラベルのテキストの色 | var(—textInverse) |
| buttonHoverBackgroundColor | CSS変数 | マウスを合わせたときにボタンの背景色 | var(—accent) |
| feedbackCorrectColor | 16進数カラー | 正解フィードバックパネルの背景色 | #D7F7E1 |
| feedbackIncorrectColor | 16進数カラー | 不正解フィードバックパネルの背景色 | #FFEBE8 |
| feedbackTextColor | 16進数カラー | フィードバックパネル内のテキストカラー | #111111 |
| optionBorderCorrectColor | 16進数カラー | 回答が表示された後の正解オプションの境界線の色 | #079355 |
| optionBorderIncorrectColor | 16進数カラー | 回答が表示された後の誤って選択されたオプションの境界線のカラー | #D73220 |
| horizontalSpacingScale | 数値文字列 | 評価コンポーネント内の水平方向の間隔の乗数 | &quot;1&quot; |
| verticalSpacingScale | 数値文字列 | 評価コンポーネント内の垂直間隔の乗数 | &quot;1&quot; |
| radiusScale | 数値文字列 | 評価コンポーネント内の境界半径の乗数 | &quot;1&quot; |

## **パレットトークンvar()参照**

これらのvar()式をエレメント値で使用して、パレットトークンを参照します。 パレットトークンを更新すると、そのトークンを使用するすべての要素が自動的に更新されます。

| **式** | **参照** |
|-------------------------|-------------------------------------|
| var(—foreground) | foundation.palette.foreground |
| var(—background) | foundation.palette.背景色 |
| var(—accent) | foundation.palette.accent |
| var(—backgroundSubtle) | foundation.palette.backgroundSubtle |
| var(—secondary) | foundation.palette.secondary |
| var(—textPrimary) | foundation.palette.textPrimary |
| var(—textInverse) | foundation.palette.textInverse |
| var(—font-heading) | foundation.fonts.heading |
| var(—font-body) | foundation.fonts.body |

## テーマjsonの例

```
{
  "id": "slate",
  "name": "Slate",
  "version": "1.0.0",
  "description": "A warm, authoritative theme with cream background, Adobe red accents, and the Roboto Slab + Roboto type system",
  "author": "Content Composer",
  "source": "custom",
  "isDefault": false,
  "foundation": {
    "palette": {
      "foreground": "#1A1A1A",
      "background": "#FAF7F2",
      "accent": "#E8001C",
      "backgroundSubtle": "#F0EBE1",
      "secondary": "#D9D3C9",
      "textPrimary": "#1A1A1A",
      "textInverse": "#FFFFFF"
    },
    "fonts": {
      "heading": "Roboto Slab, Georgia, 'Times New Roman', serif",
      "body": "Roboto, -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif"
    },
    "spacing": {
      "horizontal": {
        "xs": "4px",
        "s": "8px",
        "m": "12px",
        "l": "16px",
        "xl": "24px"
      },
      "vertical": {
        "xs": "4px",
        "s": "8px",
        "m": "16px",
        "l": "24px",
        "xl": "32px"
      }
    },
    "radius": {
      "none": "0px",
      "s": "4px",
      "m": "8px",
      "l": "16px",
      "full": "9999px"
    },
    "logo": null
  },
  "elements": {
    "text": {
      "lessonTitle": {
        "fontFamily": "var(--font-heading)",
        "fontSize": "48px",
        "fontWeight": "bold",
        "fontStyle": "normal",
        "color": "var(--textPrimary)",
        "textAlign": "center",
        "letterSpacing": "-0.01em",
        "lineHeight": "130%",
        "textDecoration": "none",
        "textTransform": "none",
        "paddingInlineStart": "0px",
        "paragraphSpacing": "0px"
      },
      "topicTitle": {
        "fontFamily": "var(--font-heading)",
        "fontSize": "40px",
        "fontWeight": "normal",
        "fontStyle": "normal",
        "color": "var(--textPrimary)",
        "textAlign": "left",
        "letterSpacing": "0",
        "lineHeight": "135%",
        "textDecoration": "none",
        "textTransform": "none",
        "paddingInlineStart": "0px",
        "paragraphSpacing": "0px"
      },
      "blockHeading": {
        "fontFamily": "var(--font-heading)",
        "fontSize": "24px",
        "fontWeight": "bold",
        "fontStyle": "normal",
        "color": "var(--textPrimary)",
        "textAlign": "left",
        "letterSpacing": "0",
        "lineHeight": "140%",
        "textDecoration": "none",
        "textTransform": "none",
        "paddingInlineStart": "0px",
        "paragraphSpacing": "0px"
      },
      "subheading": {
        "fontFamily": "var(--font-body)",
        "fontSize": "20px",
        "fontWeight": "bold",
        "fontStyle": "normal",
        "color": "var(--textPrimary)",
        "textAlign": "left",
        "letterSpacing": "0.01em",
        "lineHeight": "150%",
        "textDecoration": "none",
        "textTransform": "none",
        "paddingInlineStart": "0px",
        "paragraphSpacing": "0px"
      },
      "question": {
        "fontFamily": "var(--font-heading)",
        "fontSize": "24px",
        "fontWeight": "normal",
        "fontStyle": "normal",
        "color": "var(--textPrimary)",
        "textAlign": "left",
        "letterSpacing": "0",
        "lineHeight": "150%",
        "textDecoration": "none",
        "textTransform": "none",
        "paddingInlineStart": "0px",
        "paragraphSpacing": "0px"
      },
      "caption": {
        "fontFamily": "var(--font-body)",
        "fontSize": "13px",
        "fontWeight": "normal",
        "fontStyle": "normal",
        "color": "var(--textPrimary)",
        "textAlign": "left",
        "letterSpacing": "0.02em",
        "lineHeight": "170%",
        "textDecoration": "none",
        "textTransform": "none",
        "paddingInlineStart": "0px",
        "paragraphSpacing": "0px"
      },
      "paragraph": {
        "fontFamily": "var(--font-body)",
        "fontSize": "16px",
        "fontWeight": "normal",
        "fontStyle": "normal",
        "color": "var(--textPrimary)",
        "textAlign": "left",
        "letterSpacing": "0.01em",
        "lineHeight": "190%",
        "textDecoration": "none",
        "textTransform": "none",
        "paddingInlineStart": "0px",
        "paragraphSpacing": "0px"
      },
      "buttonLabel": {
        "fontFamily": "var(--font-body)",
        "fontSize": "14px",
        "fontWeight": "bold",
        "fontStyle": "normal",
        "color": "var(--textInverse)",
        "textAlign": "center",
        "letterSpacing": "0.06em",
        "lineHeight": "125%",
        "textDecoration": "none",
        "textTransform": "uppercase",
        "paddingInlineStart": "0px",
        "paragraphSpacing": "0px"
      }
    },
    "canvas": {
      "background": "var(--background)"
    },
    "header": {
      "background": "var(--background)",
      "border": "1px solid var(--secondary)"
    },
    "footer": {
      "background": "var(--background)",
      "border": "1px solid var(--secondary)"
    },
    "lessonHeader": {
      "background": "var(--accent)"
    },
    "topic": {
      "background": "var(--background)",
      "border": "1px solid var(--secondary)"
    },
    "navigation": {
      "background": "var(--backgroundSubtle)",
      "border": "1px solid var(--secondary)"
    },
    "button": {
      "background": "var(--accent)"
    },
    "pagination": {
      "background": "var(--backgroundSubtle)",
      "horizontalSpacingScale": "1",
      "verticalSpacingScale": "1",
      "radiusScale": "1"
    },
    "paragraphBlock": {
      "background": "transparent",
      "cardBackgroundColor": "var(--backgroundSubtle)",
      "cardBorder": "1px solid var(--secondary)",
      "cardShadowOffset": "0px 2px 6px",
      "cardShadowColor": "var(--foreground)",
      "cardShadowOpacity": "8%",
      "nestedAccentColor": "var(--accent)",
      "horizontalSpacingScale": "1",
      "verticalSpacingScale": "1",
      "radiusScale": "1"
    },
    "imageBlock": {
      "background": "transparent",
      "horizontalSpacingScale": "1",
      "verticalSpacingScale": "1",
      "radiusScale": "1"
    },
    "videoBlock": {
      "background": "transparent",
      "cardBackgroundColor": "var(--backgroundSubtle)",
      "cardBorder": "1px solid var(--secondary)",
      "cardShadowOffset": "0px 2px 6px",
      "cardShadowColor": "var(--foreground)",
      "cardShadowOpacity": "8%",
      "horizontalSpacingScale": "1",
      "verticalSpacingScale": "1",
      "radiusScale": "1"
    },
    "imageGrid": {
      "background": "transparent",
      "cardBackgroundColor": "var(--backgroundSubtle)",
      "cardBorder": "1px solid var(--accent)",
      "cardShadowOffset": "0px 2px 8px",
      "cardShadowColor": "var(--foreground)",
      "cardShadowOpacity": "8%",
      "horizontalSpacingScale": "1",
      "verticalSpacingScale": "1",
      "radiusScale": "1"
    },
    "accordion": {
      "background": "transparent",
      "cardBackgroundColor": "var(--backgroundSubtle)",
      "cardBorder": "1px solid var(--secondary)",
      "cardShadowOffset": "0px 2px 6px",
      "cardShadowColor": "var(--foreground)",
      "cardShadowOpacity": "8%",
      "horizontalSpacingScale": "1",
      "verticalSpacingScale": "1",
      "radiusScale": "1"
    },
    "carousel": {
      "background": "transparent",
      "cardBackgroundColor": "var(--backgroundSubtle)",
      "cardBorder": "1px solid var(--secondary)",
      "cardShadowOffset": "0px 2px 6px",
      "cardShadowColor": "var(--foreground)",
      "cardShadowOpacity": "8%",
      "horizontalSpacingScale": "1",
      "verticalSpacingScale": "1",
      "radiusScale": "1"
    },
    "flipCard": {
      "background": "transparent",
      "cardFrontBackgroundColor": "var(--backgroundSubtle)",
      "cardBackBackgroundColor": "var(--accent)",
      "arrowColor": "var(--textInverse)",
      "cardBorder": "1px solid var(--secondary)",
      "cardShadowOffset": "0px 2px 6px",
      "cardShadowColor": "var(--foreground)",
      "cardShadowOpacity": "8%",
      "horizontalSpacingScale": "1",
      "verticalSpacingScale": "1",
      "radiusScale": "1"
    },
    "tabs": {
      "background": "transparent",
      "activeBg": "var(--accent)",
      "inactiveBg": "var(--backgroundSubtle)",
      "containerBg": "var(--backgroundSubtle)",
      "horizontalSpacingScale": "1",
      "verticalSpacingScale": "1",
      "radiusScale": "1"
    },
    "timeline": {
      "background": "transparent",
      "cardBackgroundColor": "var(--backgroundSubtle)",
      "cardBorder": "1px solid var(--secondary)",
      "cardShadowOffset": "0px 2px 6px",
      "cardShadowColor": "var(--foreground)",
      "cardShadowOpacity": "8%",
      "trackColor": "var(--secondary)",
      "progressCompletedBg": "var(--accent)",
      "progressCurrentBorder": "var(--accent)",
      "progressUnreachedBg": "var(--secondary)",
      "progressUnreachedBorder": "var(--backgroundSubtle)",
      "horizontalSpacingScale": "1",
      "verticalSpacingScale": "1",
      "radiusScale": "1"
    },
    "assessment": {
      "background": "transparent",
      "optionTextColor": "var(--textPrimary)",
      "optionIndicatorColor": "var(--accent)",
      "optionSelectedColor": "var(--accent)",
      "optionCheckmarkColor": "var(--textInverse)",
      "optionBackgroundColor": "var(--background)",
      "optionHoverBackgroundColor": "var(--backgroundSubtle)",
      "buttonBackgroundColor": "var(--accent)",
      "buttonTextColor": "var(--textInverse)",
      "buttonHoverBackgroundColor": "var(--accent)",
      "feedbackCorrectColor": "#D7F7E1",
      "feedbackIncorrectColor": "#FFEBE8",
      "feedbackTextColor": "#111111",
      "optionBorderCorrectColor": "#079355",
      "optionBorderIncorrectColor": "#D73220",
      "horizontalSpacingScale": "1",
      "verticalSpacingScale": "1",
      "radiusScale": "1"
    }
  }
}
```
