# しし屋 フォルダ（sishiya.github.io）

しし屋のトップページ。GitHub: `sishiya/sishiya.github.io`（Public）、公開は https://sishiya.github.io/ 。2026-10-24 に作った。
ラボは別のフォルダ・リポジトリ: `../アプリ開発/`（まなびラボ）・`../ゲーム/`（あそびラボ）・`../くらし/`（くらしラボ）。

## 方針
- 名前はどのサービスも「しし屋」。ラボはその中のシリーズ（GA4 の「しし屋 ＞ しし屋シリーズ」と同じ形）。
- ここは案内だけ。アプリは置かない（置き場所はラボ）。ラボが増えたら `index.html` のカードと `sitemap.xml`・`README.md` に足す。
- 見た目はバナー案A（クリーム色の地にドット・ライオン・ラボの色: まなび 青 `#2b6cb0`／あそび オレンジ `#d9480f`／くらし 緑 `#2f855a`）。絵のもとは `../アプリ開発/_dev/sns-icon/brand-2026-10/`。
- 日本語・英語（`../アプリ開発/I18N.md` の形。`localStorage` の `manabi-lang` をラボと共有）。
- アクセス解析は GA4 `G-E2VPYKV2Y9`（`content_group:'top'`）。プライバシーポリシーはまなびラボのものにリンク。
- `robots.txt` はこのリポジトリにしか置けない（GitHub Pages の URL のいちばん上）。ラボのサイトマップができたら `Sitemap:` の行を足す。

## 進め方の約束
- 進め方は `../アプリ開発/RULES.md` を下敷きにする。
- **commit の前に毎回、公開前チェック** `tools/check-public.ps1`（pre-commit でも走る）。結果をユーザーに伝える。Public なので push＝公開。**push はユーザーがチャットで頼んだときだけ**。
- **Artifact は使わない**。公開は GitHub Pages だけ。
- 確認は `.claude/launch.json` の `top`（http://localhost:8810/）。幅 375px でも毎回。
- 返事は日本語で。
