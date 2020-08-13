# Laravel環境構築

- Laravel + Nginx + Mysql + xdebugの環境です
- dockerを使ったlaravelの環境構築なのでlaradockと名付けています

## LaraDock

1. リポジトリをクローン

   ```
   git clone https://gitlab.com/welcome-to-sodai/laravel.git laravel_app/laradock
   ```

2. laradock階層で

   ```
   cp env-example .env
   ```
   必要に応じて中身は編集

3. 同じくlaradock階層で

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

## デバッグ(vscode用)
   ```json:launch.json
   {
    // Use IntelliSense to learn about possible attributes.
    // Hover to view descriptions of existing attributes.
    // For more information, visit: https://go.microsoft.com/fwlink/?linkid=830387
    "version": "0.2.0",
    "configurations": [
        {
            "name": "Listen for XDebug",
            "type": "php",
            "request": "launch",
            "pathMappings": {
                "/var/www/": "${workspaceRoot}/src/"
            },
            "log": true,
            "port": 9000
        },
        {
            "name": "Launch currently open script",
            "type": "php",
            "request": "launch",
            "program": "${file}",
            "cwd": "${fileDirname}",
            "port": 9000
        }
    ]
   }
   ```
   以上を`launch.json`に設定するとデバッグできる。

## まとめ

- Laravelの環境構築ができた

## Next Step

- Laravelを勉強していくのみ!
- [チームラボのサイト](https://team-lab.github.io/skillup/step2/03-laravel-demo.html)で自分は最初勉強しました
- Sodai.でチュートリアル作ってくれる方募集中です...

   