# 英検1級 単語トレーナー（Androidアプリ版 / PWA）

## 構成
- index.html … アプリ本体
- words.json … サーバーから取得する単語帳（形式は下記）
- manifest.webmanifest / sw.js / icon-*.png … ホーム画面にアプリとして追加するための設定

## 使い方（5分）
1. このフォルダ一式を、HTTPSで公開できる場所に置く（GitHub Pages、Netlify、Cloudflare Pages など）。
2. Androidの Chrome で公開URLを開き、メニュー →「アプリをインストール」（または「ホーム画面に追加」）。
3. 以後はアプリアイコンから起動。単語帳は起動時にサーバーの words.json から取得し、オフラインでは前回の内容を使います。

## words.json の形式
[{"en":"abate","ja":"和らぐ","ex":"The storm began to abate.","exja":"嵐は弱まり始めた。"}, ...]
- 単語帳を更新したい時は words.json を差し替えるだけ。苦手度は英単語ごとに引き継がれます。
- 別のサーバーのURLを使う場合は、アプリ内「サーバーから単語帳を取得」にURLを入力。そのサーバーはCORS（Access-Control-Allow-Origin）を許可する必要があります。

## データの保存
苦手度・設定は端末のChrome内に保存されます。Chromeのサイトデータ消去で消えるため、アプリ内の「書き出し」で時々バックアップしてください。

## 更新時の注意
index.html を変更したら sw.js の `const C='eiken1-v1'` の数字を上げてください。

## 本物のAPK（Playストア / 配布用）が必要な場合
公開URLを https://www.pwabuilder.com に入力すると、Android用パッケージ（APK/AAB）を生成できます。
