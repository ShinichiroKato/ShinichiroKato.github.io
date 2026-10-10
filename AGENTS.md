# AGENTS.md

Shinichiro Kato の個人サイト。
GitHub Pages の標準の Jekyll 3.10 で、プロフィールとアプリの紹介、プライバシーポリシー、サポートのページを日英で置く。
URL の一覧は [README.md](README.md) を参照。

## 守ること

- Commit、Push、リポジトリの作成、GitHub Pages の設定など、公開に関わる操作は実行前に確認する。
- App Store Connect に登録した URL（`/{ja,en}/apps/<slug>/privacy/`、`/{ja,en}/apps/<slug>/support/` など）は変更も削除もしない。
- プラグイン、テーマ、GitHub Actions は足さない（GitHub Pages が既定で有効にするものだけを使う）。
- JavaScript は振り分けのページ（`_layouts/chooser.html`）だけで使い、動かなくても選べるリンクを出す。
- 解析ツールなどの追跡用のスクリプトは入れない。
- サイトに出さないファイルは、`_config.yml` の `exclude` に入れる。
- コメントには理由（Why）を書く。
  やり方（How）や、コードを読めばわかることは書かない。
  例外として、front matter と include の引数の意味は、レイアウトと include の先頭のコメントに書く。

## ビルドと確認

`_site/` と `.jekyll-cache/` は、作業を頼んだ人が手元で動かしている `jekyll serve` が使っているので消さない。
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

アプリのページを足したり書き換えたりしたら、見出しの並びがテンプレートと違うページを洗い出す。
節を消したアプリ（外部に送らない、権限を使わない）は出てくるので、ルールどおりかを確かめる。
また、テンプレートの印（`APPNAME` と `【】`）と、端末やOSの名前が残っていないことを確かめる。

```sh
for f in index privacy/index support/index; do for l in ja en; do t=$(grep '^## ' _templates/app/$l/$f.md); for d in $l/apps/*/; do [ "$(grep '^## ' "$d$f.md")" = "$t" ] || echo "$d$f.md"; done; done; done
grep -rn 'APPNAME\|【' ja/apps en/apps apps
grep -rnE 'iPhone|iPad|Mac|macOS|iOS|iPadOS' ja/apps en/apps _data/apps.yml
```

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
- サイトのページの日本語では、コロンを半角にし、後ろに半角の空白を入れる（「施行日: 」）。
  名前の引用と画面の名前は“ ”で囲み、アプリは「カレンダーアプリ」「設定アプリ」のように“ ”なしで書く。
- アプリの画面の名前は、Apple の用語と違っても、アプリの画面の表記に合わせる（Wright の“サジェスト”など）。
- アプリの動きや画面の名前は、そのアプリのリポジトリ（取扱説明書、文字列カタログ）で確かめる。
  確かめられないことは書かない。
- 名前は英語表記にする。
  日本語のページでは、名前だけを出す要素（見出し、カード、タグ、署名など）に `lang="en"` を付ける。
  文の中に混ざる名前には付けない。
- 施行日は `<time datetime="2026-10-04">2026年10月4日</time>` のように書く。

アクセシビリティは WCAG 2.2 AA に合わせる。
そのうえで、次を守る。

- 文章の中のリンクには下線を付ける。
  一覧やナビゲーションのリンクは、マウスを重ねたときだけ下線を出す。
- カードはリンクを 1 つだけ持つ。

## アプリのページの形

アプリのページは `_templates/app/` のテンプレートから作り、すべてのアプリで形をそろえる。

- `##` の見出しは、テンプレートと同じ名前と順にする。
  足したり言い換えたりしない。
  - 紹介：主な機能、こんなときに、プライバシー、ご利用にあたって（Key Features、Great For、Privacy、Good to Know）
  - プライバシーポリシー：収集する情報、外部に送信する情報、権限、データの削除、問い合わせフォーム（Information Collected、Information Sent Outside the App、Permissions、Deleting Your Data、Contact Form）
  - サポート：テンプレートのまま、アプリの名前だけを変える。
- プライバシーポリシーで、外部に送らないアプリは「外部に送信する情報」の節と、`description` の「外部に送る情報」を消す。
  権限を使わないアプリは「権限」の節を消す。
- 端末やOSの名前（iPhone、iPad、Mac、iOS、macOSなど）は書かない。
  対応する端末やOSが変わっても、ページを直さずに済むようにするため。
  カレンダーアプリのように、Appleのアプリの名前として書くのはよい。
- 紹介ページの導入文は `description` に書く。
  レイアウトが本文の先頭に出すので、本文には書かない。
- 紹介ページの本文の最初の文は「〇〇（読み）は、〜です。」「〇〇 is 〜.」の形にする。
- 紹介ページの `###` は、何ができるかがわかる短い言い方にする。
  数は決めない。
- 「こんなときに」の項目は「〜する」の形（英語は「-ing」）で書く。
- 「ご利用にあたって」には、許可しないと使えない権限、使えない条件、自動で作る内容の正確さの注意を書き、最後に免責の文を置く。
- テンプレートにある決まった文（紹介の「ご利用にあたって」の免責の文、プライバシーポリシーの冒頭の文、問い合わせフォームの節、末尾の注記など）は、文言を変えない。
  どのアプリにも同じように当てはまるので、1つだけ変えるとアプリの間で説明が食い違う。
  アプリだけのことは、決まった文を変えずに段落を足して書いてよい。
- テンプレートにない文でも、ほかのアプリと同じことを言うときは、同じ言い回しにする。
- 権限の名前は次の表に合わせる。
  新しい権限は、設定アプリでの表示に合わせて表に足す。
  Face IDやTouch IDのような方式は、名前ではなく説明の文に書く。

| 日本語 | 英語 |
| --- | --- |
| カメラ | Camera |
| メディアとApple Music | Media & Apple Music |
| 生体認証 | Biometrics |
| カレンダー（フルアクセス） | Calendars (Full Access) |
| 位置情報（このアプリの使用中） | Location (While Using the App) |
| 通知 | Notifications |

テンプレートにない文でアプリの間でそろえた言い回しは、次のとおり。
〇〇には、アプリや送信先の名前が入る。

| 内容 | 日本語 | 英語 |
| --- | --- | --- |
| iCloudでの同期 | iCloudを使用して、同じApple Accountでサインインしているデバイス間で同期（ポリシーでは「利用者のiCloudを使用して」） | sync across your devices signed in to the same Apple Account, using iCloud（ポリシーでは using your iCloud account） |
| 同期しないもの | このデバイスにのみ保存し、同期しません（受け身の文では「同期されず、このデバイスにのみ保存されます」） | stored only on this device and not synced |
| 同期先も含めた削除 | iCloudを使用するすべてのデバイスから削除されます | deleted from all of your devices using iCloud |
| IPアドレス | 〇〇には、利用者のIPアドレスも伝わる場合があります | 〇〇 may also receive your IP address |
| 送信先のポリシー | 〇〇のプライバシーポリシー（複数なら各サービスのプライバシーポリシー）に従って取り扱われます | handled in accordance with 〇〇’s Privacy Policy (each service’s privacy policy) |
| 許可を求めるとき | 〜したときに許可を求めます | 〇〇 asks for permission when 〜 |
| 権限を許可しない場合 | それ以外の機能は使用できます | you can still use the rest of the app |
| アプリを削除する前に | 〇〇を削除する前に | before you delete 〇〇（同じ文に〇〇が続くときは the app） |

## ポリシーを改定するとき

- 日本語と英語の両方を直し、末尾の施行日を更新する。
- テンプレートの決まった文や、決まった言い回しの表を変えるときは、すべてのアプリの日英のページとテンプレート、表を一度に直す。
- App Store Connect の「App のプライバシー」の回答と矛盾しないか、作業を頼んだ人に確認を頼む。

## アプリを追加する手順

日本語、英語、振り分けのページをすべてそろえてから、最後に `_data/apps.yml` に足す。
足した時点で、アプリ一覧にカードが並ぶからだ。

1. テンプレートをコピーし、`APPNAME` をアプリの名前に置き換える。
   レイアウトは、URL の slug で `_data/apps.yml` のアプリを引く。

   ```sh
   cp -R _templates/app/ja ja/apps/<slug>
   cp -R _templates/app/en en/apps/<slug>
   cp -R _templates/app/chooser apps/<slug>
   grep -rl APPNAME ja/apps/<slug> en/apps/<slug> apps/<slug> | xargs sed -i '' 's/APPNAME/<名前>/g'
   ```

2. `【】` の印を、紹介とポリシーの本文に書き換える（「アプリのページの形」に従う）。
   ページ間のリンクは相対で書いてあるので、そのままでよい。
3. `apps/<slug>/icon.png` を 256×256、8bit の PNG で置く。
   Icon Composer の `.icon` からは次のように書き出せる（`ictool` は Xcode の Icon Composer.app の中にある）。

   ```sh
   ictool AppIcon.icon --export-image --output-file icon.png --platform iOS --rendition Default --width 128 --height 128 --scale 2
   magick icon.png -depth 8 -strip PNG32:icon.png
   ```

4. `_data/apps.yml` に slug、名前、カテゴリ（日英）、サブタイトル（日英）を足す。
   問い合わせフォーム（Googleフォーム）の“アプリ”の選択肢にも名前を足す。
   サポートページのリンクとアプリの“問題を報告”は、この欄に名前を入れてフォームを開くので、選択肢にないと入らない。
   同じ理由で、フォームの欄は消したり作り直したりしない（アプリのコードが欄の ID を使っている）。
5. App Store で公開したら、`app_store_id` を足す。
   紹介ページのアイコンの下に App Store のバッジと QR コードが出て、Smart App Banner も出る。
   QR コードは `apps/<slug>/qr.svg` に置く。
   [Apple のマーケティングツール](https://toolbox.marketingtools.apple.com/)が QR コードに使う短縮リンク（`itsct=apps_box_qrcode` を付けたリンクを `apple.co` で短くしたもの）から作る。

   ```sh
   npx qrcode -t svg -e M -q 4 -o apps/<slug>/qr.svg "https://apple.co/xxxxxxx"
   ```
