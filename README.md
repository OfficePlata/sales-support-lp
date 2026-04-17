# セールスサポート LP

売り込まない、再現性のあるセールスを提供するオンラインサロンのランディングページ。

**本番URL:** https://sales-support-lp.pages.dev

## 技術スタック

- HTML / CSS / Vanilla JS（依存ライブラリなし）
- Cloudflare Pages（ホスティング）
- Stripe（決済）

## ファイル構成

```
├── index.html       # メインLP
├── tokusho.html     # 特定商取引法に基づく表記
├── _redirects       # Cloudflare Pages リダイレクト設定
└── _headers         # セキュリティヘッダー設定
```

## セットアップ

### 1. Stripe決済URLの設定

`index.html` の以下2行を実際のPayment Link URLに変更：

```js
const STRIPE_MONTHLY = 'https://buy.stripe.com/（月額リンク）';
const STRIPE_YEARLY  = 'https://buy.stripe.com/（年額リンク）';
```

Stripeダッシュボード → **Payment Links** でリンクを作成してコピー。

### 2. 特定商取引法の事業者情報入力

`tokusho.html` を開いて以下を入力：
- 販売業者名
- 運営責任者氏名
- 所在地・電話番号・メールアドレス

## デプロイ

```bash
# 初回
npx wrangler pages project create sales-support-lp --production-branch main

# 更新
git add . && git commit -m "update" && git push
```

pushすると Cloudflare Pages が自動でビルド・デプロイします（GitHub連携設定後）。

## 関連システム

バックエンド（Stripe Webhook × GAS × LINE）は別リポジトリで管理：
https://github.com/OfficePlata/sales-support-lp
