# これは何か

Railsアプリの開発がしやすいDockerfileとdocker-compose.ymlです。
元ネタは[joker1007さんのQiitaの記事](https://qiita.com/joker1007/items/9f54e763ae640f757cfb)。

# 使い方

1. ルートディレクトリにある`Dockerfile.sample`、`docker-compose.yml.sample`、`Gemfile.sample`をそれぞれ`Dockerfile`、`docker-compose.yml`、`Gemfile`に名前変更します。
2. `docker-compose build`でイメージを作成します。
3. `docker-compose run --rm web bundle exec rails new . --force --no-deps --database=postgresql`でRailsアプリの雛形を生成します。
  - 個人的な好みとしては、`docker-compose run --rm web bundle exec rails new . --force --no-deps --database=postgresql --skip-action-mailer --skip-action-mailbox --skip-action-text --skip-active-storage --skip-action-cable --skip-spring --skip-turbolinks --skip-test --skip-bootsnap`ってな感じで生成することが多いです。
  - 細かいオプションは覚えていないので、毎回`rails new -h`して各種オプションを確認しています。

# ポイント

- `bundle install`するときのパスや`node_modules`のパスを`docker-compose.yml`内のvolumesとして指定していること
  - 新しいGemを追加したりするときに毎回`docker build`するのは面倒くさいなと思っていて、なんとかならないですか？と相談したところ、`bundle install`先をvolumeで指定すればOKと教わりました。
