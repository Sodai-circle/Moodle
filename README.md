# Laravel環境構築

- Moodle + Nginx + Mysqlの環境です

## moodock

1. リポジトリをクローン

   ```
   git clone https://github.com/Sodai-circle/Moodle.git moodle_app/moodock
   ```

2. moodock階層で

   ```
   cp env-example .env
   ```
   必要に応じて中身は編集(特にAPP_NAME)

3. 同じくmoodock階層で

   ```
   docker-compose build workspace nginx mysql
   ```

4. コンテナを構築、起動

   ```
   docker-compose up -d workspace nginx mysql
   ```

5. workspaceのbashに入りmoodleアプリをhtmlディレクトリへ

   ```
   docker-compose exec workspace bash
   cp -R /opt/moodle /var/www/html/
   chown -R www-data /var/moodledata
   chmod -R 777 /var/moodledata
   chmod -R 0755 /var/www/html/moodle
   exit
   ```


8. 初期設定

   [ここ](http://localhost/moodle)

- mysqlなど諸々の設定をする

- 全ての設定が終わった後、systemみたいな簡素な画面が表示される。それをしばらく待った後に`http://localhost/admin/index.php?cache=0&confirmrelease=1&confirmplugincheck=1`ここにアクセスしないといけない? 

## 使い方

- 始めるとき moodockの階層で
   ```bash
   docker-compose up -d workspace nginx mysql
   ```
- 終わるとき
   ```bash
   docker-compose down
   ```

## Next Step

- [公式サイト](https://docs.moodle.org/39/en/Main_page)
- API周りは[ここ](https://docs.moodle.org/39/en/Web_services)

   
