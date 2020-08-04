# Laravel環境構築

- Laravel + Nginx + Mysqlの環境です
- dockerを使ったlaravelの環境構築なのでlaradockと名付けています

## LaraDock

1. リポジトリをクローン

   ```
   git clone https://gitlab.com/welcome-to-sodai/laravel.git laravel_app/laradock
   ```

2. .envをコピー

   ```
   cp env-example .env
   ```

3. laradock階層で

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

6. src配下の.envを編集

   ```
   DB_CONNECTION=mysql
   DB_HOST=mysql
   DB_PORT=3306
   DB_DATABASE=default
   DB_USERNAME=default
   DB_PASSWORD=secret
   ```

7. config/app.phpの一部編集

   ```
   'timezone' => 'Asia/Tokyo',
   'locale' => 'ja',
   ```

8. うまくいっているか確認

   [ここ](http://localhost/)

## 使い方

- 始めるとき laradockの階層で
   ```bash
   docker-compose up -d workspace nginx mysql
   ```
- 終わるとき
   ```bash
   docker-compose down
   ```

## まとめ

- Laravelの環境構築ができた

## Next Step

- Laravelを勉強していくのみ!
- [チームラボのサイト](https://team-lab.github.io/skillup/step2/03-laravel-demo.html)で自分は最初勉強しました
- Sodai.でチュートリアル作ってくれる方募集中です...

   