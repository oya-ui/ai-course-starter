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

## フォルダ構成の前提

```
ai-course-starter/        ← Cursor はここを開いたまま（閉じない）
├── .cursor/skills/       ← スキルが常に有効
├── mvp/                  ← Step1〜3 のドキュメント（ここを参照）
│   ├── STEP1.md
│   ├── STEP2.md
│   └── STEP3_UI_MOCK.html
└── my-mvp/               ← Step4 でここに Next.js アプリを作る
    ├── app/
    ├── package.json
    └── .env.local
```

**Cursor は `ai-course-starter` を開いたまま作業する。** `my-mvp` に切り替える必要はない。

---

## 入力の確認

最初に（ai-course-starter ルートから）以下を読む（ない場合はユーザーに貼ってもらう）。

- `mvp/STEP2.md`（画面 ID・除外リスト）
- `mvp/STEP3_UI_MOCK.html`（画面レイアウトの意図）
- `mvp/STEP1.md`（主導線・ログイン/DB の有無）

**読み終わったら以降のコマンドは `my-mvp/` の中で実行する。** `cd my-mvp` を都度明示する。

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
- git が入っているか確認 → `git --version` を実行してもらう
  - 入っていない場合 → `docs/GIT_SETUP.md` を参照
- Supabase / Vercel アカウントがあるか確認
  - ない場合 → `docs/SUPABASE_SETUP.md` / `docs/VERCEL_SETUP.md` を参照

### 2. プロジェクト作成

**ai-course-starter のルートで実行する**（`cd` 不要、今いる場所でそのまま）。

```bash
# プロジェクト名は自由に変えてOK（my-mvp のままでも可）
npx create-next-app@latest my-mvp --tailwind --app --no-src-dir --no-import-alias
cd my-mvp
```

> **TypeScript について**: 対話形式で聞かれたら「No」（JavaScript を選ぶ）で問題なし。型エラーに詰まらず開発できる。

### 3. my-mvp を独立した GitHub リポジトリにする

`my-mvp/` は ai-course-starter とは別の git リポジトリにする（Vercel がここを接続する）。

```bash
# my-mvp の中で実行
cd my-mvp     # ← まだいない場合
git init
git add .
git commit -m "initial commit"
```

その後、GitHub で空のリポジトリを作り（ai-course-starter とは別）、以下を実行：

```bash
git remote add origin https://github.com/<ユーザー名>/<リポジトリ名>.git
git push -u origin main
```

詳細は `docs/GIT_SETUP.md` を参照。

### 4. 実装計画を作る

`mvp/STEP4.md`（ai-course-starter ルートに保存）に以下を書く。

```markdown
# MVP Step4 実装計画

## 画面 → ルート対応
| 画面 ID | ファイルパス（my-mvp/ 内） |
|---------|--------------------------|
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
```

### 5. パッケージインストール

```bash
cd my-mvp     # ← 必ず my-mvp の中で実行
npm install @supabase/supabase-js
```

### 6. .env.local を作る

`.env.local` は `my-mvp/` の直下に作る。

**.env.local の作り方（OS別）**

- **Cursor のファイルツリーを使う（推奨）**: `my-mvp/` フォルダを右クリック → 「New File」→ `.env.local` と入力
- Mac（ターミナル）: `touch my-mvp/.env.local`
- Windows PowerShell: `New-Item my-mvp/.env.local`
- Windows コマンドプロンプト: `type nul > my-mvp\.env.local`

作成後、ファイルを開いて以下を入力（値は Supabase の API ページからコピー）：

```
NEXT_PUBLIC_SUPABASE_URL=https://xxxx.supabase.co
NEXT_PUBLIC_SUPABASE_ANON_KEY=eyJhbGciOi...
```

**秘密情報（APIキー）をチャットやコードに直接書かない。** `.env.local` は create-next-app が自動で `.gitignore` に入れてくれるため GitHub に漏れない。

### 7. 実装（主導線1本を最優先）

- まず S1 から S2 の流れが「動く」状態を作る
- モックの見た目は「だいたい近ければ OK」（完全一致は不要）
- エラーが出たら**ターミナルのエラーメッセージをコピーしてチャットに貼る**

### 8. ローカル確認

```bash
cd my-mvp     # ← 必ず my-mvp の中で実行
npm run dev
```

ブラウザで `http://localhost:3000` を開いて主導線が動くか確認。

> 別のプロジェクトで `npm run dev` が動いていると 3000 番ポートが塞がれる。その場合は自動的に 3001 で起動するので案内に従う。

### 9. Vercel デプロイ

1. `my-mvp/` 内の変更を GitHub に push する
   ```bash
   cd my-mvp
   git add .
   git commit -m "implement mvp"
   git push
   ```
2. Vercel で `my-mvp` の GitHub リポジトリを接続する
   - **ai-course-starter ではなく my-mvp のリポジトリを選ぶ**
3. 環境変数を Vercel の UI で設定
4. デプロイ → HTTPS URL を確認

詳細は `docs/VERCEL_SETUP.md` を参照。

---

## デプロイでつまずいた時

| 症状 | 確認ポイント |
|------|------------|
| ビルド失敗 | `cd my-mvp && npm run build` でローカル再現 → 直してから再デプロイ |
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
- ai-course-starter の git リポジトリに my-mvp のコードを push しない
