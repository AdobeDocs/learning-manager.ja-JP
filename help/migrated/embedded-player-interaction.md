---
jcr-language: en_us
title: 埋め込みプレーヤーインタラクション API に関するドキュメント
description: 埋め込みプレーヤーでイベントをリッスンし、アクションをトリガーする様々なAPIについて説明します
contentowner: chandrum
exl-id: 4734ecc1-cc8a-40b0-8997-32a31ec661ec
source-git-commit: 3d183dc40e4d1962d25160b74d8cf6cfa26e3171
workflow-type: tm+mt
source-wordcount: '833'
ht-degree: 69%

---

# 埋め込みプレーヤーインタラクション API に関するドキュメント

Adobe Learning Manager には、アプリケーションに統合できるライブラリが用意されています。 このライブラリには、埋め込みプレーヤーでイベントをリッスンし、アクションをトリガーするための各種 API が用意されています。

用意されている API をプレーヤーで使用して、再生や一時停止などのアクションを実行できます。

## ライブラリの読み込み

ライブラリは[こちら](https://cpcontents.adobe.com/public/publiccdn/playerInteractionLib.min.js)から入手できます。

ライブラリを読み込むには、次の手順を実行します。

1. js ファイルをコンシューマーアプリケーションに読み込みます。
2. ライブラリを読み込むと、window.cpPlayerLib が取り込まれます。

>[!NOTE]
>
>製品USを使用していない場合は、パラメータcpPlayerLib.envとcpPlayerLib.sourceOriginをenvに基づいて設定します。

デフォルト値は次のとおりです。

* window.cpPlayerLib.env = [https://learningmanager.adobe.com/app/player](https://learningmanager.adobe.com/app/player)
* window.cpPlayerLib.sourceOrigin = &quot;[https://cpcontents.adobe.com](https://cpcontents.adobe.com/)&quot;

### 利用可能なメソッド

cpPlayerLib ライブラリは、次の関数で構成されています。

**startPlayer**

<table>
<tbody>
<tr>
<td>メソッド名</td>
<td>startPlayer</td>
</tr>
<tr>
<td>説明</td>
<td>アプリにプレーヤーを読み込みます。</td>
</tr>
<tr>
<td>パラメーター</td>
<td><li>loId：学習オブジェクト ID。</li><li>accountId：ALM アカウントのアカウント ID。</li><li>userId：ユーザー ID。</li><li>accessToken：アクセストークン。</li><li>domRefId：プレーヤーをレンダリングする必要がある div コンテナーの ID。</li><li>onModuleLoaded：以下の詳細が含まれているモジュールが読み込まれると、この関数が呼び出されます。</li><br><li>contentType</li><li>loId</li><li>moduleId</li><li>completed</li><li>currentLanguage</li><li>availableLanguages</li><li>isCCAvailable</li><li>ccEnabled</li></br></td>
</tr>
<tr>
<td>戻り値</td>
<td>promise を返します。 プロミスの解決に伴い、playerObjが渡されます。</td>
</tr>
<tr>
<td>例外</td>
<td>その約束は例外を引き起こすだろう。</td>
</tr>
<tr>
<td>サンプルコード</td>
<td>cpPlayerLib.startPlayer(loId, accountId, userId, accessToken, domRefId, onModuleLoaded).then((playerObj) =&gt; {//playerObjにはプレーヤーと対話するためのAPIがあります}) &gt;</td>
</tr>
</tbody>
</table>

**getAllPlayers**

<table>
<tbody>
<tr>
<td>メソッド名</td>
<td>getAllPlayers</td>
</tr>
<tr>
<td>説明</td>
<td>現在のページのすべてのplayerオブジェクトを返します。</td>
</tr>
<tr>
<td>パラメーター</td>
<td>なし</td>
</tr>
</tr>
<tr>
<td>サンプルコード</td>
<td>cpPlayerLib.getAllPlayers()</td>
</tr>
</tbody>
</table>

**getPlayer**


<table>
<tbody>
<tr>
<td>メソッド名</td>
<td>getPlayer</td>
</tr>
<tr>
<td>説明</td>
<td>指定された学習オブジェクトIDを持つPlayerオブジェクトを返します。</td>
</tr>
<tr>
<td>パラメーター</td>
<td><li>loId：学習オブジェクト ID。</li></td>
</tr>
</tr>
<tr>
<td>サンプルコード</td>
<td>cpPlayerLib.getPlayer(loId)</td>
</tr>
</tbody>
</table>

**navigateToModule**

<table>
<tbody>
<tr>
<td>メソッド名</td>
<td>navigateToModule</td>
</tr>
<tr>
<td>説明</td>
<td>次のモジュールに移動します。</td>
</tr>
<tr>
<td>パラメーター</td>
<td><li>moduleId:モジュールID。</li></td>
</tr>
</tr>
<tr>
<td>サンプルコード</td>
<td>playerObj.navigateToModule(moduleID)</td>
</tr>
</tbody>
</table>

**次へ**

<table>
<tbody>
<tr>
<td>メソッド名</td>
<td>next</td>
</tr>
<tr>
<td>説明</td>
<td>次のモジュールに移動します。</td>
</tr>
<tr>
<td>パラメーター</td>
<td><li>なし</li></td>
</tr>
</tr>
<tr>
<td>サンプルコード</td>
<td>playerObj.next()</td>
</tr>
</tbody>
</table>

**前の**

<table>
<tbody>
<tr>
<td>メソッド名</td>
<td>previous</td>
</tr>
<tr>
<td>説明</td>
<td>前のモジュールに移動します。</td>
</tr>
<tr>
<td>パラメーター</td>
<td><li>なし</li></td>
</tr>
</tr>
<tr>
<td>サンプルコード</td>
<td>playerObj.previous()</td>
</tr>
</tbody>
</table>

**toggleTOC**

<table>
<tbody>
<tr>
<td>メソッド名</td>
<td>toggleTOC</td>
</tr>
<tr>
<td>説明</td>
<td>プレーヤーで目次パネルを切り替えます。</td>
</tr>
<tr>
<td>パラメーター</td>
<td><li>なし</li></td>
</tr>
</tr>
<tr>
<td>サンプルコード</td>
<td>playerObj.toggleTOC()</td>
</tr>
</tbody>
</table>

**toggleNotes**

<table>
<tbody>
<tr>
<td>メソッド名</td>
<td>toggleNotes</td>
</tr>
<tr>
<td>説明</td>
<td>プレーヤーでメモパネルを切り替えます。</td>
</tr>
<tr>
<td>パラメーター</td>
<td><li>なし</li></td>
</tr>
</tr>
<tr>
<td>サンプルコード</td>
<td>playerObj.toggleNotes()</td>
</tr>
</tbody>
</table>

**toggleClosedCaption**

<table>
<tbody>
<tr>
<td>メソッド名</td>
<td>toggleClosedCaption</td>
</tr>
<tr>
<td>説明</td>
<td>プレーヤーでのクローズドキャプションの表示を切り替えます。</td>
</tr>
<tr>
<td>パラメーター</td>
<td><li>なし</li></td>
</tr>
</tr>
<tr>
<td>サンプルコード</td>
<td>playerObj.toggleClosedCaption()</td>
</tr>
</tbody>
</table>

**changeLanguage**

<table>
<tbody>
<tr>
<td>メソッド名</td>
<td>changeLanguage</td>
</tr>
<tr>
<td>説明</td>
<td>プレーヤーのコンテンツ言語を変更します。</td>
</tr>
<tr>
<td>パラメーター</td>
<td><li>language：指定する言語コード。</li></td>
</tr>
</tr>
<tr>
<td>サンプルコード</td>
<td>playerObj.changeLanguage("es")</td>
</tr>
</tbody>
</table>

**closePlayer**

<table>
<tbody>
<tr>
<td>メソッド名</td>
<td>closePlayer</td>
</tr>
<tr>
<td>説明</td>
<td>プレーヤーを閉じ、ページから削除します。 </td>
</tr>
<tr>
<td>パラメーター</td>
<td><li>なし</li></td>
</tr>
</tr>
<tr>
<td>サンプルコード</td>
<td>playerObj.closePlayer()</td>
</tr>
</tbody>
</table>

**togglePlayPause**

<table>
<tbody>
<tr>
<td>メソッド名</td>
<td>togglePlayPause</td>
</tr>
<tr>
<td>説明</td>
<td>プレーヤー上のコンテンツの再生と一時停止を切り替えます。</td>
</tr>
<tr>
<td>パラメーター</td>
<td><li>なし</li></td>
</tr>
</tr>
<tr>
<td>サンプルコード</td>
<td>playerObj.togglePlayPause()</td>
</tr>
</tbody>
</table>

**setVolume**

<table>
<tbody>
<tr>
<td>メソッド名</td>
<td>setVolume</td>
</tr>
<tr>
<td>説明</td>
<td>プレーヤーの音量を設定します。 値は 0 から 1 の範囲で設定します。</td>
</tr>
<tr>
<td>パラメーター</td>
<td><li>volume：ボリュームの値。 有効な範囲は0 ～ 1です。 </li></td>
</tr>
</tr>
<tr>
<td>サンプルコード</td>
<td>playerObj.setVolume(0.5)</td>
</tr>
</tbody>
</table>

**setPlayBackSpeed**

<table>
<tbody>
<tr>
<td>メソッド名</td>
<td>setPlayBackSpeed</td>
</tr>
<tr>
<td>説明</td>
<td>プレーヤーでの再生速度を設定します。</td>
</tr>
<tr>
<td>パラメーター</td>
<td><li>speed：指定する速度の値。 有効な値は、.25、.5、.75、1、1.25、1.5、1.75、2です。</li></td>
</tr>
</tr>
<tr>
<td>サンプルコード</td>
<td>playerObj.setPlayBackSpeed(1.25)</td>
</tr>
</tbody>
</table>

**シーク**

<table>
<tbody>
<tr>
<td>メソッド名</td>
<td>seek</td>
</tr>
<tr>
<td>説明</td>
<td>ビデオで任意の時間にジャンプします。</td>
</tr>
<tr>
<td>パラメーター</td>
<td><li>time：ジャンプ先の時間。 時間は秒単位です。</li></td>
</tr>
</tr>
<tr>
<td>サンプルコード</td>
<td>playerObj.seek(50)</td>
</tr>
</tbody>
</table>

**転送**

<table>
<tbody>
<tr>
<td>メソッド名</td>
<td>forward</td>
</tr>
<tr>
<td>説明</td>
<td>ビデオを 10 秒早送りします。</td>
</tr>
<tr>
<td>パラメーター</td>
<td><li>なし</li></td>
</tr>
</tr>
<tr>
<td>サンプルコード</td>
<td>playerObj.forward()</td>
</tr>
</tbody>
</table>

**下位**

<table>
<tbody>
<tr>
<td>メソッド名</td>
<td>backward</td>
</tr>
<tr>
<td>説明</td>
<td>ビデオを 10 秒早戻しします。</td>
</tr>
<tr>
<td>パラメーター</td>
<td><li>なし</li></td>
</tr>
</tr>
<tr>
<td>サンプルコード</td>
<td>playerObj.backward()</td>
</tr>
</tbody>
</table>

**navigateToPage**

<table>
<tbody>
<tr>
<td>メソッド名</td>
<td>navigateToPage</td>
</tr>
<tr>
<td>説明</td>
<td>PPT / PDF で指定したページにジャンプします。</td>
</tr>
<tr>
<td>パラメーター</td>
<td><li>pageNumber:ジャンプ先のページ番号を指定します。</li></td>
</tr>
</tr>
<tr>
<td>サンプルコード</td>
<td>playerObj.navigateToPage (5)</td>
</tr>
</tbody>
</table>

**nextPage**

<table>
<tbody>
<tr>
<td>メソッド名</td>
<td>nextPage</td>
</tr>
<tr>
<td>説明</td>
<td>PPT / PDF で次のページにジャンプします。</td>
</tr>
<tr>
<td>パラメーター</td>
<td><li>なし</li></td>
</tr>
</tr>
<tr>
<td>サンプルコード</td>
<td>playerObj.nextPage()</td>
</tr>
</tbody>
</table>

**前のページ**

<table>
<tbody>
<tr>
<td>メソッド名</td>
<td>previousPage</td>
</tr>
<tr>
<td>説明</td>
<td>PPT / PDF で前のページにジャンプします。</td>
</tr>
<tr>
<td>パラメーター</td>
<td><li>なし</li></td>
</tr>
</tr>
<tr>
<td>サンプルコード</td>
<td>playerObj.previousPage()</td>
</tr>
</tbody>
</table>

**ズームイン**

<table>
<tbody>
<tr>
<td>メソッド名</td>
<td>zoomIn</td>
</tr>
<tr>
<td>説明</td>
<td>PPT / PDF でコンテンツを拡大します。</td>
</tr>
<tr>
<td>パラメーター</td>
<td><li>なし</li></td>
</tr>
</tr>
<tr>
<td>サンプルコード</td>
<td>playerObj.zoomIn()</td>
</tr>
</tbody>
</table>

**ズームアウト**

<table>
<tbody>
<tr>
<td>メソッド名</td>
<td>zoomOut</td>
</tr>
<tr>
<td>説明</td>
<td>PPT / PDF でコンテンツを縮小します。</td>
</tr>
<tr>
<td>パラメーター</td>
<td><li>なし</li></td>
</tr>
</tr>
<tr>
<td>サンプルコード</td>
<td>playerObj.zoomOut()</td>
</tr>
</tbody>
</table>

**downloadJobAid**

<table>
<tbody>
<tr>
<td>メソッド名</td>
<td>downloadJobAid</td>
</tr>
<tr>
<td>説明</td>
<td>コースから作業計画書をダウンロードします。</td>
</tr>
<tr>
<td>パラメーター</td>
<td><li>なし</li></td>
</tr>
</tr>
<tr>
<td>サンプルコード</td>
<td>playerObj.downloadJobAid()</td>
</tr>
</tbody>
</table>

**toggleJobAidPullout**

<table>
<tbody>
<tr>
<td>メソッド名</td>
<td>toggleJobAidPullout</td>
</tr>
<tr>
<td>説明</td>
<td>作業計画書をダウンロードするかどうかを指定します。</td>
</tr>
<tr>
<td>パラメーター</td>
<td><li>なし</li></td>
</tr>
</tr>
<tr>
<td>サンプルコード</td>
<td>playerObj.toggleJobAidPullout()</td>
</tr>
</tbody>
</table>

**全画面表示**

<table>
<tbody>
<tr>
<td>メソッド名</td>
<td>fullScreen</td>
</tr>
<tr>
<td>説明</td>
<td>プレーヤーをフルスクリーンモードに設定します。</td>
</tr>
<tr>
<td>パラメーター</td>
<td><li>なし</li></td>
</tr>
</tr>
<tr>
<td>サンプルコード</td>
<td>playerObj.fullScreen()</td>
</tr>
</tbody>
</table>

## イベントのリスト

**onPlayerEvents(callBack)**

登録すると、プレーヤーイベントすべてでコールバック関数が呼び出されます。 イベント名は次のとおりです。

* PLAY（ビデオ/オーディオ/ CP）
* PAUSE（ビデオ/オーディオ/ CP）
* TIMEUPDATE（ビデオ/オーディオ/ CP）
* PAGECHANGE（PPT / PDF）
* NOTEADDED（すべてのコンテンツ）
* LAUNCHED（すべてのコンテンツ）
* STARTED（すべてのコンテンツ）
* COMPLETED（すべてのコンテンツ）
* PASSED（すべてのコンテンツ）
* FAILED（すべてのコンテンツ）

**onStreamingEvents(callBack)**

登録すると、ユーザーのアクティビティを追跡するために送信されるプレーヤーステートメントすべてで、コールバック関数が呼び出されます。
