# 陽月の知って占うタロット豆知識

HTML・CSS・Vanilla JavaScriptのみで動く静的サイトです。外部APIやビルドは不要です。大アルカナ22枚の正位置で占います。

## ファイル構成

公開用のファイルは `dist/` 内です。

```
dist/
  index.html
  css/style.css
  js/app.js
  js/cards.js
  images/card-back.png
  images/cards/0.png ～ 21.png
  images/hizuki-sheet.png  ← ご提供の陽月キャラクターシート
```

## ローカル確認

`dist/index.html` をブラウザで開くだけで動きます。スマートフォン表示はブラウザの開発者ツールで幅390px程度にして確認できます。開始→4ジャンルのいずれか→カード→クイズ→メッセージ→再占いを試してください。

## 画像の差し替え

- 陽月：ご提供のキャラクターシートを `dist/images/hizuki-sheet.png` に配置済みです。トップ・案内・結果のメッセージに上半身を表示します。コメントは吹き出し形式で、スマートフォンは立ち絵の下、PCは立ち絵の横に表示します。元画像を加工せず、CSSの `.hizuki-portrait` と `.guide-character img` で表示範囲を指定しています。別の画像に差し替える場合は `js/app.js` の `HIZUKI_IMAGE` と、この表示範囲を調整してください。単独の顔画像にする場合は `.avatar img` の width を100%、height を100%、left とtopを0、object-fitをcoverにします。
- 表面：`images/cards/0.png` ～ `21.png` を同名で差し替えます。カード番号の対応は `js/cards.js` の並びです。`object-fit: contain` で縦横比を保ちます。
- 裏面：`images/card-back.png` を差し替えます。別名にする場合は `js/app.js` の `CARD_BACK` を変更してください。

## 文章・リンクの変更

- タイトル：`index.html` の title と `js/app.js` の `SITE_TITLE`、home関数内の見出しを変更します。
- クイズ：`js/cards.js` の各カードの `quizOptions` に3つの選択肢を指定し、`quizAnswer` に正解の位置（0・1・2）を指定します。データ上の正解位置は8枚・7枚・7枚に分散しています。画面ではさらに表示順を混ぜます。
- 解説：各カードの `explanation` を編集してください。22枚すべてに初心者向けの約80〜160文字の解説を用意しています。
- ミニ占い：各カードの `readingLove`（恋愛）、`readingWork`（仕事）、`readingRelationship`（人間関係）、`readingSelf`（今の自分）を直接編集してください。88種類すべて独立した約180〜320文字の鑑定文です。共通の文章を自動で当てはめる方式は使っていません。
- ココナラ：`js/app.js` の `COCONALA_URL` に `https://coconala.com/users/5319059` を設定済みです。新しいタブで陽月 Hizukiのプロフィールを開きます。
- 色・余白：`css/style.css` の先頭のCSS変数から調整できます。

現在はカードそのものの代表的な意味を使い、正位置・逆位置の区別はしていません。将来は各カードに `upright` / `reversed` のオブジェクトを追加し、その中に解説・鑑定文を置いて表示を切り替えられます。小アルカナを追加する場合は `CARDS` に同じ構造のオブジェクトと画像を追加してください。抽選件数に22という固定値は使っていません。

## GitHub Pages

1. GitHubでリポジトリを作成します。
2. `dist/` の**中身**をリポジトリのルートへアップロードします（index.htmlがルートに来る形）。
3. Settings → Pages → Deploy from a branchを選びます。
4. mainブランチ、`/ (root)` を指定しSaveします。
5. 公開処理の完了後、Pagesに表示されるURLを開きます。

## 一般的なレンタルサーバー

FTPまたはサーバーのファイル管理画面で、`dist/` の中身を `public_html`、`www` など契約先の公開フォルダーへアップロードしてください。既存のindex.htmlがある場合は上書き前にバックアップを取ってください。サブフォルダーでも動く相対パス構成です。

サイトには個人情報の入力、通信による占い、データ保存はありません。画像はご提供のZIPの素材を使っています。


