# これは何か

Railsアプリの開発がしやすいDockerfileとdocker-compose.ymlです。
元ネタは[joker1007さんのQiitaの記事](https://qiita.com/joker1007/items/9f54e763ae640f757cfb)。

# 使い方

1. ルートディレクトリにある`Dockerfile.sample`、`docker-compose.yml.sample`、`Gemfile.sample`をそれぞれ`Dockerfile`、`docker-compose.yml`、`Gemfile`に名前変更します。
2. `docker-compose build`でイメージを作成します。
3. `docker-compose run --rm web bundle exec rails new . --force --database=postgresql`でRailsアプリの雛形を生成します。
