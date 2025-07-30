環境構築手順
　本プロジェクトの開発環境はDockerを使用して構築します。以下の手順に従ってセットアップしてください。

 1.コンテナの起動
 　　$ docker-compose up -d --build
   　$ code .
  　   Docker Desktopを開き、contact-formコンテナが稼働していることを確認してください。
 
 2.PHPコンテナにログイン→Laravelパッケージのインストール
     $ docker-compose exec php bash
     $ composer install
 　    ※composer.jsonに記載されたパッケージのリストがインストールされます。
 
 3..envファイルの作成と設定
     $ cp .env.example .env
     $ exit
       .envファイルを開き、以下のように修正してください。
     DB_CONNECTION=mysql
     DB_HOST=mysql
     DB_PORT=3306
     DB_DATABASE=laravel_db
     DB_USERNAME=laravel_user
     DB_PASSWORD=laravel_pass

 4.データベース設定確認（phpMyAdmin)
       以下のURLにアクセスし、データベースが存在することを確認します
     http://localhost:8080

 5.マイグレーションの実行
 　    phpコンテナ内で以下のコマンドを入力して、マイグレーションを実行してください。
     $ php artisan migrate
       ※http://local:8080/にアクセスすると、docker-compose.ymlで設定した、phpMyAdmin を開くことができます。
       phpMyAdmin では、ウェブブラウザからデータベースに接続して、閲覧等することができます。
