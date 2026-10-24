# しし屋のトップを作って公開するまでの手順（2026-10-24 に実際にやったこと）

作りなおすとき・新しいラボや入口のサイトを足すときの見本。だれがやるかを「ユーザー」「Claude」で書く。

## 1. 置き場所を決める
- GitHub Pages で URL のいちばん上（`https://sishiya.github.io/`）になるのは、リポジトリ名が **`sishiya.github.io`** のときだけ。ほかの名前だと `/<名前>/` の下になる。
- ラボ（`manabi-lab`・`asobi-lab`・`kurashi-lab`）は別のリポジトリのまま。URL は変わらない。容量（1GB）もリポジトリごと。
- PC では `Documents/Claude/しし屋/`（ラボのフォルダと並べる）。

## 2. 中身を作る（Claude）
- 道具はくらしラボから写す: `.gitignore`・`.gitattributes`・`.githooks/pre-commit`・`tools/check-public.ps1`・`.claude/serve.ps1`、`LICENSE`（まなびラボ）。`.private-words.txt` もくらしラボから写す（Git に入れない）。
- `index.html`（日本語・英語。言語の決め方はまなびラボの `I18N.md`、`manabi-lang` を共有）、`404.html`、`robots.txt`、`sitemap.xml`、`assets/`（ライオン・OGP）、`README.md`・`CLAUDE.md`・`LICENSE-CONTENT`、`.nojekyll`。
- GA4 はラボと同じ ID（`content_group:'top'`）。
- 確かめる: パソコン・幅 375px（headless の Edge は 500px くらいより狭くならないので、幅 375px は Claude のブラウザの画面で）・ダークモード・英語・404。
- `git init -b main` → `git config core.hooksPath .githooks` → `git config core.quotepath false` → `git remote add origin https://github.com/sishiya/sishiya.github.io.git` → 公開前チェック → 最初のコミット。

## 3. リポジトリを作る（ユーザー）
- https://github.com/new 。Owner `sishiya`、名前 **`sishiya.github.io`**、**Public**、README・.gitignore・license は**付けない**（空のまま）。
- この PC の `gh` はログインしていないので、リポジトリは Claude からは作れない。

## 4. push する（ユーザーが「push して」と言ったときだけ、Claude）
- `MANABI_PUSH_OK=1 git -C "<フォルダ>" push -u origin main`
  - まなびラボの guard（`.claude/hooks/guard.pl`）は、コマンドが `MANABI_PUSH_OK=1` で**始まる**ときだけ push を通す。`cd … ;` を前に付けると止まるので `git -C` を使う。
- 最初の公開は push から約30秒。`https://sishiya.github.io/` が 200 になるまで待って、ファイル・404・ラボの URL を確かめる。
- Settings → Pages は「Deploy from a branch」・`main`・`/ (root)`（この名前のリポジトリは最初からそうなる）。

## 5. Search Console（ユーザー。タグは Claude）
- プロパティを追加 →「URL プレフィックス」`https://sishiya.github.io/`。
- 確認の方法は **「HTML タグ」**。「Google アナリティクス」は**通らない**（GA4 をスクリプトから読みこむ形なので、ページの HTML に gtag.js のタグがない。2026-10-24 にエラーになった）。
- HTML タグの値は Google アカウントごとに同じで、まなびラボと同じ `dD02qa-…` だった。`index.html` の `<head>` に入れる → コミット → push（ユーザーの GO）→ 公開に出たら（約45秒）「確認」。
- 通ったら「サイトマップ」に `sitemap.xml` を送る。
- 2026-10-24: HTML タグで確認が通った（プロパティのページが開いた）。

## 6. 名前・リンクをそろえる（ユーザー）
- X・Zenn・note・DEV のウェブサイトの欄を `https://sishiya.github.io/` に。YouTube の説明文は Claude が `youtube-upload.ps1 -Channel` で。
- 名前・バナー・ヘッダーを「しし屋」にそろえた分は、まなびラボの `_dev/sns-icon/brand-2026-10/`（`TODO-user.md` がサービス別のやること、`PROPOSAL.md` が決めた理由）。
  - YouTube のチャンネルの英語は `en_US` で送る（`en` だと消える）。brandingSettings と翻訳は別々に送る（いっしょだと 400）。名前は API で変えられない。
  - note のヘッダーは、パソコンでもスマホでもまん中の細い帯しか出ない（幅が広い画面だと高さの 1/4 くらい）。文字は1段にまとめる。
