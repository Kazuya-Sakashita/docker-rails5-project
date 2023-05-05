# README


## ターミナル操作

### build の実行
`docker-compose build`


### コンテナの起動
`docker-compose up -d`
Dockerfileの中のcommandでrailsサーバー起動があるため、コンテナ起動させると開発用サーバーが起動する。



### データベースの作成
`docker-compose run web bundle exec rails db:create`

ブラウザのアドレスバーに `localhost:3000` と入力し、起動を確認.
いつもの画面が表示されればOKです。少し読み込みに時間がかかる場合があります。


### dockerでの開発
ターミナル操作は、コンテナ内のターミナルに接続して実施する必要があります。
このプロジェクトでは下記コマンドで接続できます。
`docker-compose exec web bash`









### webコンテナ立ち上がらないエラーが途中発生したため下記対応実施
`docker-compose up`で起動する。-dなしにするとターミナルにログが表示される。-dはバックグラウンドでの起動となる。

`Function not implemented - Failed to initialize inotify (Errno::ENOSYS)`エラー発生

config/environments/development.rbのファイルを編集する。
```
 - config.file_watcher = ActiveSupport::EventedFileUpdateChecker
 + config.file_watcher = ActiveSupport::FileUpdateChecker
```
