# docker_practice
これは、Docker と Docker Compose の学習を目的として、自己学習で作成したプロジェクトです。

このプロジェクトは、Nginx ウェブサーバーと Flask アプリケーションサーバーによる基本的な Docker Compose のセットアップを示しています。

## サービス

* **webserver**
    * コンテナ名: web-container
    * イメージ: nginx:latest
    * ポート: 9000:80
    * ボリューム: ./webserver/nginx.conf:/etc/nginx/nginx.conf (Nginx の設定)
    * 依存関係: appserver
    * ネットワーク: mynetwork
* **appserver**
    * コンテナ名: app-container
    * ビルド: ./appserver (appserver ディレクトリ内の Dockerfile からビルド)
    * ポート: 5000:5000
    * ボリューム: ./appserver:/app (appserver ディレクトリをコンテナにマウント)
    * 環境変数: FLASK\_APP=app.py
    * ネットワーク: mynetwork

## ネットワーク

* **mynetwork**: webserver と appserver が通信するために使用するネットワーク。

## アプリケーションサーバー

アプリケーションサーバーは、シンプルな Flask アプリケーションです。

* '/' ルートを定義し、"Hello, World!" を返します。
* コンテナ内でホスト '0.0.0.0'、ポート 5000 で動作します。
* `requirements.txt` を介してインストールされる Flask を使用します。

## 必要条件

* Flask

## セットアップ

1.  Docker と Docker Compose がインストールされていることを確認します。
2.  このリポジトリをクローンします。
3.  `docker-compose up --build` を実行して、サービスをビルドし、起動します。
4.  ブラウザで `http://localhost:9000` にアクセスして、アプリケーションを表示します。