# ApeStone 公式LP

Google Play デベロッパー/アプリの所有権確認用に作成した簡易LPです。

## ファイル構成

- `index.html` … トップページ（会社概要・事業内容・ゲーム紹介）
- `privacy.html` … プライバシーポリシー（テンプレート、要カスタマイズ）
- `style.css` … 共通スタイル

## 公開前に埋めるべき項目

`index.html` 内の以下のコメント箇所を実際の情報に差し替えてください。

- アパレル事業の説明文
- 代表者名・所在地・お問い合わせメールアドレス（会社概要テーブル）
- Google Play ストアURL（公開後）

`privacy.html` はテンプレートです。実際に収集している情報・利用しているSDK（AdMob/Firebase/課金など）と相違がないか必ず確認し、必要であれば法務確認のうえ内容を調整してください。

## GitHub Pages への公開手順

1. このフォルダの内容でGitHubリポジトリを作成（例: `apestone-site`）
2. リポジトリの `Settings > Pages` で公開ブランチを設定（例: `main` / `root`）
3. 数分後、`https://<ユーザー名>.github.io/<リポジトリ名>/` で公開されます

```bash
cd lp-apestone
git init
git add .
git commit -m "Initial LP"
git branch -M main
git remote add origin https://github.com/<ユーザー名>/apestone-site.git
git push -u origin main
```

## Google Play 所有権確認（Search Console経由）への対応

Play Consoleで開発者/アプリの所有権確認を行う際、Googleは対象サイトの
所有権をGoogle Search Console経由で確認させることがあります。方式は主に2つです。

### 方式A: HTMLタグ（metaタグ）

1. Google Search Console でプロパティを追加し、「所有権確認」→「HTMLタグ」を選択
2. 発行された `<meta name="google-site-verification" content="..." />` をコピー
3. `index.html` の `<head>` 内、コメントで示した箇所に貼り付けてデプロイ

### 方式B: HTMLファイルのアップロード

1. Search Console で「所有権確認」→「HTMLファイル」を選択し、`google********.html` をダウンロード
2. そのファイルを `index.html` と同じ階層（サイトのルート）にそのまま配置してデプロイ
3. `https://<公開URL>/google********.html` にアクセスできることを確認してから、Search Console側で確認を実行

いずれの方式もGitHub Pagesで問題なく機能します。確認が完了した後にタグ/ファイルを削除すると
再確認時にエラーになる場合があるため、基本的にはそのまま残しておくことをおすすめします。
