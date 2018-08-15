splatnet2statink-gcr
================

splatoonの戦績同期をGoogle App Engine上で行うことができます。

[splatnet2statink](https://github.com/frozenpandaman/splatnet2statink)をGAE上で動作させています。

#  使い方

## Google Cloud Platformでプロジェクトを作成

詳細は割愛

## Google Cloud SDKを導入

詳細は割愛

## `secret.yaml`を作成しsplatnet2statinkで取得した情報をセットします。

このファイルは、`app.yaml`のincludesに設定されるため安全に秘密情報を設定します。

```yaml
# secret.yaml
env_variables:
  api_key: "my_api_key_here"
  cookie: "my_cookie_here"
  user_lang: "en-US"
  session_token: "my_session_token_here"
```

## App Engineにデプロイ

アプリケーションのデプロイ
```
$ gcloud app deploy
(もしくは $ gcloud app deploy app.yaml)
```

cronのデプロイ
`cron.yaml`を設定することで、一定時間ごとに`/sync`にGETリクエストを送信することができます。この機能を使って自動同期を実現しています。

```
$ gcloud app deploy cron.yaml
```

## App Engineの設定

DDoSなどを食らっても悲しいので、ファイアウォールで外部アクセスを切ったりapp.yamlを編集してスケーリングなどを各種調整してください。

# ライセンス

[GPLv3](https://www.gnu.org/licenses/gpl-3.0.html)


