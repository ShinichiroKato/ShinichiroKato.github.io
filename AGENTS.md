# AGENTS.md

Shinichiro Kato の個人サイト。
GitHub Pages の標準の Jekyll 3.10 で、プロフィールと iOS アプリの紹介、プライバシーポリシー、サポートのページを日英で置く。
URL の一覧は [README.md](README.md) を参照。

## 守ること

- push、リポジトリの作成、GitHub Pages の設定など、公開に関わる操作は実行前に確認する。
- App Store Connect に登録した URL（`/{ja,en}/apps/<slug>/privacy/`、`/{ja,en}/apps/<slug>/support/` など）は変更も削除もしない。
- プラグイン、テーマ、GitHub Actions は足さない（GitHub Pages が既定で有効にするものだけを使う）。
- JavaScript は振り分けのページ（`_layouts/chooser.html`）だけで使い、動かなくても選べるリンクを出す。
- 解析ツールなどの追跡用のスクリプトは入れない。
- サイトに出さないファイルは、`_config.yml` の `exclude` に入れる。
- コメントには理由（Why）を書く。やり方（How）や、コードを読めばわかることは書かない。
  例外として、front matter と include の引数の意味は、レイアウトと include の先頭のコメントに書く。

## ビルドと確認

`_site/` と `.jekyll-cache/` は、作業依頼者が手元で動かしている `jekyll serve` が使っているので消さない。
確認用のビルドは一時フォルダーに作る。

```sh
bundle exec jekyll build --destination <一時フォルダー>
npx html-validate "<一時フォルダー>/**/*.html"
```

html-validate の次の指摘は、HTML5 では正しいので対象外とする。

- **doctype-style**：小文字の `<!doctype html>`
- **valid-id**：数字で始まる見出しの `id`
- **no-trailing-whitespace**：Liquid が出す行末の空白
- **void-style**：kramdown が出す `<img />` と `<br />`

`jekyll serve` が動いているときは、Lighthouse でも確かめる。

```sh
npx lighthouse http://localhost:4000/ja/ --only-categories=accessibility,best-practices,seo
```

`jekyll serve` では `canonical` などの URL が `localhost` になる。
`jekyll build` では `_config.yml` の `url` になる。

## ページの書き方

- すべてのページを日本語と英語でそろえる。
  404 だけは言語を分けず、1 ページに「404」と英語の一文だけを置く。
- サイトの中のリンクは、同じ言語のページへ直接張る。
- slug は英小文字とハイフンだけ。
- front matter の意味は、`_layouts/default.html` と `_layouts/chooser.html` の先頭のコメントにある。
- アプリのページは、見出しを `##` から書く（`h1` とアイコンはレイアウトが出す）。
  プロフィールとアプリ一覧は `h1` を本文に書く。
- クラスは段落やリストの次の行に `{: .note}` のように付ける。
  使えるのは `style.css` にあるクラスだけ。
- サイトのページの日本語では、英数字との間に空白を入れない（Apple の日本語の表記に合わせる）。
- 名前は英語表記にし、日本語のページでは `lang="en"` を付ける。
- 施行日は `<time datetime="2026-10-04">2026年10月4日</time>` のように書く。

アクセシビリティは WCAG 2.2 AA に合わせる。
そのうえで、次を守る。

- 文章の中のリンクには下線を付ける。
  一覧やナビゲーションのリンクは、マウスを重ねたときだけ下線を出す。
- カードはリンクを 1 つだけ持つ。

## ポリシーを改定するとき

- 日本語と英語の両方を直し、末尾の施行日を更新する。
- App Store Connect の「App のプライバシー」の回答と矛盾しないか、作業を頼んだ人に確認を頼む。

## アプリを追加する手順

日本語、英語、振り分けのページをすべてそろえてから、最後に `_data/apps.yml` に足す。
足した時点で、アプリ一覧にカードが並ぶからだ。

1. `ja/apps/dropin/`、`en/apps/dropin/`、`apps/dropin/` をコピーし、フォルダー名を `<slug>` に変える。
   レイアウトは、URL の slug で `_data/apps.yml` のアプリを引く。
2. front matter の `title` と `description`、紹介、ポリシー、サポートの本文を書き換える。
   ページ間のリンクは相対で書いてあるので、そのままでよい。
3. `apps/<slug>/icon.png` を 256×256、8bit の PNG で置く。
   Icon Composer の `.icon` からは次のように書き出せる（`ictool` は Xcode の Icon Composer.app の中にある）。

   ```sh
   ictool AppIcon.icon --export-image --output-file icon.png --platform iOS --rendition Default --width 128 --height 128 --scale 2
   magick icon.png -depth 8 -strip PNG32:icon.png
   ```

4. `_data/apps.yml` に slug、名前、カテゴリ（日英）、サブタイトル（日英）を足す。
5. App Store で公開したら、`app_store_id` を足す。
   紹介ページのアイコンの下に App Store のバッジと QR コードが出て、Smart App Banner も出る。
   QR コードは `apps/<slug>/qr.svg` に置く。
   [Apple のマーケティングツール](https://toolbox.marketingtools.apple.com/)が QR コードに使う短縮リンク（`itsct=apps_box_qrcode` を付けたリンクを `apple.co` で短くしたもの）から作る。

   ```sh
   npx qrcode -t svg -e M -q 4 -o apps/<slug>/qr.svg "https://apple.co/xxxxxxx"
   ```
