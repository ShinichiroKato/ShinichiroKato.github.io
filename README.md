# ShinichiroKato.github.io

Shinichiro Kato の個人サイト <https://shinichirokato.github.io/> のソース。
プロフィールと、公開している iOS アプリの紹介、プライバシーポリシー、サポートのページを置いている。
GitHub Pages の標準の Jekyll で作っている。

Issues と Pull Request は受け付けていない。
ページの書き方、アプリの追加、公開前の確認などの作業の決まりは [AGENTS.md](AGENTS.md) を参照。

## URL

言語をパスの先頭に置く。
言語のない URL は、ブラウザーの言語に合わせて `/ja/` か `/en/` へ移る振り分けのページになる。

```
/{ja,en}/                      プロフィール
/{ja,en}/apps/                 アプリ一覧
/{ja,en}/apps/<slug>/          アプリの紹介
/{ja,en}/apps/<slug>/privacy/  プライバシーポリシー
/{ja,en}/apps/<slug>/support/  サポート
/、/apps/、/apps/<slug>/...     振り分け
```

App Store Connect などに登録する URL は、言語を明示したものにする。
登録した URL は変更も削除もしない。

## 手元での表示

Ruby と Bundler が必要。
次のコマンドで <http://localhost:4000/> に表示される。

```sh
bundle config set --local path vendor/bundle
bundle install
bundle exec jekyll serve
```

## 公開

`main` ブランチに push すると、GitHub Pages がリポジトリのルートからサイトを作り直す。

## ライセンス

- **コード**（HTML、CSS、JavaScript、Liquid のテンプレート、設定ファイル）：[MIT License](LICENSE)
- **サイトに表示される文章と画像**：MIT License の対象外で、無断転載を禁じる。
