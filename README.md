# Laravel

1. リポジトリをクローン

   ```
   git clone https://gitlab.com/welcome-to-sodai/laravel.git laravel_app/laradock
   ```

2. .envをコピー

   ```
   cp env-example .env
   ```

3. raildock階層で

   ```
   docker-compose build workspace nginx mysql
   ```

4. コンテナを構築、起動

   ```
   docker-compose up -d workspace nginx
   ```

5. workspaceのbashに入りlaravelアプリを作成

   ```
   docker-compose exec workspace bash
   composer create-project laravel/laravel . --prefer-dist
   exit
   ```

6. うまくいっているか確認

   [ここ](http://localhost/)

7. src配下の.envを編集

   ```
   DB_CONNECTION=mysql
   DB_HOST=mysql
   DB_PORT=3306
   DB_DATABASE=default
   DB_USERNAME=default
   DB_PASSWORD=secret
   ```

8. config/app.phpの一部編集

   ```
   'timezone' => 'Asia/Tokyo',
   'locale' => 'ja',
   ```

   