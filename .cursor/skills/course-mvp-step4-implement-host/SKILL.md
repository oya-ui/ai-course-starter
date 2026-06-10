---
name: course-mvp-step4-implement-host
description: >-
  Step3 のモック了承後、Next.js + Supabase で実装し Vercel にデプロイする。初心者向け。
  Use for Step4, 実装, コーディング, デプロイ, Vercel, Supabase, npm, Next.js, 本番公開, ホスティング, Step3 の次.
---

# AIコース — Step4（実装 → ホスティング）

## 目的

`mvp/STEP3_UI_MOCK.html` のモックを本番の Next.js アプリに変え、
**HTTPS の公開 URL が開くところまで**初心者でも迷わず進めるよう伴走する。

---

## 入力の確認

最初に以下を読む（ない場合はユーザーに貼ってもらう）。

- `mvp/STEP2.md`（画面 ID・除外リスト）
- `mvp/STEP3_UI_MOCK.html`（画面レイアウトの意図）
- `mvp/STEP1.md`（主導線・ログイン/DB の有無）

---

## 標準スタック（インライン定義）

| 役割 | ツール | 理由 |
|------|--------|------|
| フレームワーク | Next.js 14（App Router） | Vercel と相性が良い・日本語情報が多い |
| スタイル | Tailwind CSS | クラス名だけで書ける・初心者向き |
| DB / 認証 | Supabase | 無料枠あり・管理画面で操作できる |
| ホスティング | Vercel | GitHub 連携でボタン1つでデプロイ |

---

## 全体フロー（必ず順番通りに）

### 1. 事前確認

- Node.js / npm が入っているか確認 → `node -v` を実行してもらう
  - 入っていない場合 → `docs/NODE_SETUP.md` を開いてセットアップしてから戻る
- Supabase / Vercel アカウントがあるか確認
  - ない場合 → `docs/SUPABASE_SETUP.md` / `docs/VERCEL_SETUP.md` を参照

### 2. プロジェクト作成

```bash
# ターミナルで実行（プロジェクト名は何でもOK）
npx create-next-app@latest my-mvp --typescript --tailwind --app --no-src-dir --no-import-alias
cd my-mvp
```

### 3. 実装計画を作る

`mvp/STEP4.md` に以下を書く（書いてから実装に入る）。

```markdown
# MVP Step4 実装計画

## 画面 → ルート対応
| 画面 ID | ファイルパス |
|---------|------------|
| S1 | app/page.tsx |
| S2 | app/list/page.tsx |

## データ設計（簡易 ER）
| テーブル名 | 主なカラム |
|-----------|-----------|
| （例）items | id, title, created_at |

## 環境変数キー名（値は書かない）
- NEXT_PUBLIC_SUPABASE_URL
- NEXT_PUBLIC_SUPABASE_ANON_KEY

## 優先順位
1. S1（主導線の起点）
2. S2（主導線の終点）
3. 必要なら S3…
```

### 4. パッケージインストール

```bash
npm install @supabase/supabase-js
```

### 5. 実装（主導線1本を最優先）

- まず S1 から S2 の流れが「動く」状態を作る
- モックの見た目は「だいたい近ければ OK」（完全一致は不要）
- **秘密情報（API キー・パスワード）をチャットやコードに直接書かない**
  → `.env.local` ファイルに書いて、ファイル名を `.gitignore` に追加する

### 6. ローカル確認

```bash
npm run dev
```

ブラウザで `http://localhost:3000` を開いて主導線が動くか確認。
エラーが出たら**ターミナルのエラーメッセージをコピーしてチャットに貼る**。

### 7. Vercel デプロイ

1. GitHub にコードを push（プロジェクトを GitHub リポジトリにしておく）
2. [vercel.com](https://vercel.com) → 「Import Git Repository」
3. 環境変数を Vercel の UI で設定（`.env.local` の内容を Vercel 側に入力）
4. 「Deploy」ボタンを押す
5. デプロイ完了後、HTTPS URL をブラウザで開いて動作確認

詳細は `docs/VERCEL_SETUP.md` を参照。

---

## デプロイでつまずいた時

| 症状 | 確認ポイント |
|------|------------|
| ビルド失敗 | ローカルで `npm run build` を実行してエラーを再現 → 直してから再デプロイ |
| 本番だけ動かない | Vercel の環境変数のキー名に typo がないか確認 |
| データが出ない | Supabase の URL / anon key・テーブル名・RLS 設定を確認 |

→ 3回直しても解消しない場合はメンターに相談する。

---

## Step4 完了の宣言

HTTPS URL でアプリが動いたら：

> Step4 完了。公開 URL: （URL）
> `mvp/STEP4.md` のチェックリストをすべて満たしています。

---

## やらないこと

- Step3 の了承前に実装だけ先に進めない
- `.env.local` の**値**をチャットやコードに直接載せない
- エラーを無視して次のステップに進まない（必ずログを読んで直す）
