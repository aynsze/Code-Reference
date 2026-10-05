
| UserScript         | 役割                                |
| -------------- | --------------------------------- |
| `@name`        | Userscriptの名前                     |
| `@namespace`   | スクリプトを識別する名前空間                    |
| `@version`     | スクリプトのバージョン                       |
| `@description` | スクリプトの説明                          |
| `@match`       | 実行対象のURL                          |
| `@include`     | 実行対象のURL                          |
| `@exclude`     | 実行対象から除外するURL                     |
| [`@run-at`](#run-at)      | 実行タイミング                           |
| [`@grant`](#grant)       | 使用するTampermonkey API              |
| `@connect`     | `GM_xmlhttpRequest`などで通信を許可するドメイン |
| `@require`     | 外部JavaScriptファイルを読み込む             |
| `@resource`    | 外部リソースを定義する                       |

---

## @grant
TampermonkeyのAPIや特別な機能を使用することを宣言する設定  
```js
// @grant        GM_notification
```

| `@grant`                                  | 意味                            |
| ----------------------------------------- | ----------------------------- |
| `none`                                    | Tampermonkey APIを使用しない        |
| [`GM_notification`](#gm_notification)     | デスクトップ通知を表示する                 |
| [`GM_xmlhttpRequest`](#gm_xmlhttprequest) | ページの制限を受けずにHTTPリクエストを送信する     |
| [`GM_download`](#gm_download)             | ファイルをダウンロードする                 |
| [`GM_setClipboard`](#gm_setclipboard)     | クリップボードにデータを書き込む              |
| [`unsafeWindow`](#unsafewindow)           | Webページ側の`window`オブジェクトにアクセスする |


- ### GM_notification
	デスクトップ通知
  | パラメータ  | 説明                             |
  | ----------- | -------------------------------- |
  | `text`      | 通知の本文                       |
  | `title`     | 通知のタイトル                   |
  | `image`     | アイコン画像（URL）              |
  | `timeout`   | 自動で消えるまでの時間（ミリ秒） |
  | `onclick`   | 通知をクリックした時の処理       |
  | `highlight` | `true` で通知を強調表示          |
  | `silent`    | `true` で通知音を鳴らさない          |

	例
	```js
	GM_notification({
		title: "エラー",
		text: "追加に失敗しました",
		timeout: 4000
	});
	```
	---


- ### GM_xmlhttpRequest
	HTTPリクエストを送信  
	アクセス先のドメインは `@connect` でも許可する必要がある
	| パラメータ       | 説明                       |
	| ----------- | ------------------------ |
	| `method`    | HTTPメソッド（`GET`、`POST`など） |
	| `url`       | リクエスト先URL                |
	| `headers`   | HTTPヘッダー                 |
	| `data`      | 送信するデータ                  |
	| `onload`    | リクエスト成功時の処理              |
	| `onerror`   | リクエスト失敗時の処理              |
	| `ontimeout` | タイムアウト時の処理               |
	| `timeout`   | タイムアウト時間（ミリ秒）            |

	例
	```js
	GM_xmlhttpRequest({
		method: "POST",
		url: "https://example.com/api",
		headers: {
				"Content-Type": "application/json"
		},
		data: JSON.stringify({
				name: "test"
		}),
		onload: (response) => {
				console.log(response.responseText);
		}
	});
	```
	---
		
- ### GM_download
	ファイルをダウンロードする
	| パラメータ       | 説明                          |
	| ----------- | --------------------------- |
	| `url`       | ダウンロードするファイルのURL            |
	| `name`      | 保存するファイル名                   |
	| `saveAs`    | `true`で保存先・ファイル名をユーザーに選択させる |
	| `onload`    | ダウンロード完了時の処理                |
	| `onerror`   | ダウンロード失敗時の処理                |
	| `ontimeout` | タイムアウト時の処理                  |
	| `timeout`   | タイムアウト時間（ミリ秒）               |

	```js
	GM_download({
		url: "https://example.com/example.txt",
		name: "example.txt"
	});
	```
	---
	
- ### GM_setClipboard
	文字列をクリップボードにコピー
	```js
	GM_setClipboard("コピーする文字列");
	```
	---

- ### unsafeWindow
	Userscriptのサンドボックスから、Webページ側の `window` オブジェクトにアクセスするために使用  
	- unsafeWindowはページ側のJavaScriptと直接やり取りする必要がある場合などに使用
	- セキュリティ上の理由から、必要な場合だけ使用するのがおすすめ

## @run-at
Userscriptをいつ実行するかを指定
```js
// @run-at       document-start
```
| `@run-at`        | 実行タイミング                                |
| ---------------- | -------------------------------------- |
| `document-start` | HTMLの読み込みが開始された直後                      |
| `document-body`  | `body`要素が存在するようになった時点                  |
| `document-end`   | HTMLの読み込みが完了し、`DOMContentLoaded`が発生した頃 |
| `document-idle`  | ページの読み込みがほぼ完了し、ブラウザがアイドル状態になった頃        |
