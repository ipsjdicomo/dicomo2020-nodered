DICOMO2020ダッシュボード
=======================

## 概要

DICOMO2020で使用したダッシュボードのソース、および環境構築用のファイルです。
Zoom APIを用いて、各セッションの参加者数を取得して表示します。
一部、ミーティングID、Token等がそのまま埋め込まれていますが、現在は無効になっています。

## 環境構築

Docker Composeを用いて環境を構築できます。
docker-compose.ymlがあるフォルダで、

> docker-compose up -d

でNode-REDサーバが起動します。
デフォルトではポート1880で動作します。

## 実行方法

実際に利用するには、以下の部分を変更する必要があります。

- Node-REDへのログインパスワード
    - data/settings.js のadminAuthを変更
    - パスワードのハッシュ化についてはNode-REDのドキュメントを参照
- ダッシュボードへのログインパスワード
    - data/settings.js のhttpNodeAuthを変更
- Zoom APIを呼び出すためのToken
    - サブフローの参加者数取得の中のset msg.tokenにJWT Tokenを指定してください。
- 各ZoomミーティングのミーティングID、参加のためのURL
    - ミーティングID設定を呼び出す前に、msg.payloadにミーティングID、msg.urlにURLを設定します。
    - あとはtemplateなどを使って、表示する内容を組み立ててください。

## ライセンス

- 全てのファイルは MIT License で利用が可能です。
- 著作権はDICOMO2020実行委員会が所有します。
