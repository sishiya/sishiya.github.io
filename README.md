# sishiya.github.io（しし屋のトップ）

しし屋の入口のページ。ブラウザで動くアプリの3つのラボへの案内だけを置いています。Claude（Claude Code）と一緒に作っています。

- 公開: https://sishiya.github.io/ （GitHub Pages。このリポジトリ名 `sishiya.github.io` が URL のいちばん上になる）
- ラボ（それぞれ別のリポジトリ）:
  - [まなびラボ](https://sishiya.github.io/manabi-lab/)（`sishiya/manabi-lab`）— 理科のアプリ
  - [あそびラボ](https://sishiya.github.io/asobi-lab/)（`sishiya/asobi-lab`）— 小さなゲーム
  - [くらしラボ](https://sishiya.github.io/kurashi-lab/)（`sishiya/kurashi-lab`）— くらしの道具

| ファイル | 中身 |
|---|---|
| `index.html` | トップ（日本語・英語。言語はラボと同じ `manabi-lang` を使う） |
| `404.html` | 見つからないときのページ（ラボに 404 がないときもこれが出る） |
| `robots.txt`・`sitemap.xml` | 検索エンジン向け。robots.txt は URL のいちばん上にしか置けないので、ラボのサイトマップもここに並べる |
| `assets/` | ライオンのアイコン（`lion.svg`）、OGP の画像（`og.svg` → `og.png`、1200×630） |
| `tools/check-public.ps1` | 公開前チェック（pre-commit で走る） |
| `SETUP.md` | 作って公開するまでの手順（リポジトリ・push・Search Console・名前そろえ） |

## はじめてクローンしたとき

```
git config core.hooksPath .githooks
git config core.quotepath false
```

## ライセンス

- ページの仕組み: MIT（`LICENSE`）
- 中身（名前・文章・アイコン・画像・文書）: CC BY-NC 4.0（`LICENSE-CONTENT`）
