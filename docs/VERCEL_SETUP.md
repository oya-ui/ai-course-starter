# Vercel セットアップガイド

Vercel は Next.js アプリを無料でインターネットに公開できるサービスです。
GitHub と連携することで、コードを push するだけで自動的にデプロイできます。

---

## 事前準備

- GitHub アカウントがあること
- ローカルのプロジェクトが GitHub リポジトリになっていること
  - なっていない場合：GitHub Desktop で「Publish Repository」をする

---

## 1. アカウントを作る

1. [vercel.com](https://vercel.com) を開く
2. 「Sign Up」→「Continue with GitHub」でサインアップ

---

## 2. プロジェクトをインポートする

1. Vercel ダッシュボードで「Add New...」→「Project」をクリック
2. 「Import Git Repository」から自分の GitHub リポジトリを探す
3. 「Import」をクリック

---

## 3. 環境変数を設定する

デプロイ前に、**Supabase の API キーを Vercel 側に登録**します。

1. 「Configure Project」画面の「Environment Variables」を展開
2. 以下の2つを追加：
   - `NEXT_PUBLIC_SUPABASE_URL` → Supabase の Project URL
   - `NEXT_PUBLIC_SUPABASE_ANON_KEY` → Supabase の anon key
3. 「Add」で追加

> `.env.local` の内容をそのまま Vercel の画面に入力します。ファイル自体はアップロード不要です。

---

## 4. デプロイする

1. 「Deploy」をクリック
2. ビルドが始まります（1〜3 分）
3. 成功すると `https://your-project.vercel.app` のような URL が表示されます

---

## 5. 動作確認

1. 表示された HTTPS URL をクリック
2. ブラウザでアプリが開くか確認
3. 主導線（Step2 で決めた A → B → C）が動くか確認

---

## デプロイが失敗した場合

1. Vercel の「Build Logs」をクリックしてエラーを確認
2. エラーメッセージをコピーしてチャットに貼る
3. ローカルでも `npm run build` を実行してエラーを再現する

**よくある原因**

| 症状 | 対処 |
|------|------|
| 環境変数が見つからないエラー | Vercel の Environment Variables にキー名の typo がないか確認 |
| TypeScript エラー | ローカルで `npm run build` してエラーを直してから再 push |
| Supabase への接続エラー | URL / anon key が正しいか・RLS の設定を確認 |

---

## 再デプロイ

コードを修正して GitHub に push すると**自動的に再デプロイ**されます。
手動でデプロイするには Vercel ダッシュボードの「Redeploy」ボタンを使います。
