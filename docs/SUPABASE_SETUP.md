# Supabase セットアップガイド

Supabase は DB（データベース）と認証を無料で使えるサービスです。
Step4 の実装で「データを保存する」ために使います。

---

## 1. アカウントを作る

1. [supabase.com](https://supabase.com) を開く
2. 「Start your project」をクリック
3. GitHub アカウントでサインアップ（推奨）

---

## 2. 新しいプロジェクトを作る

1. ダッシュボードで「New project」をクリック
2. 以下を入力：
   - **Name**: プロジェクト名（例: `my-mvp`）
   - **Database Password**: 強いパスワードを設定（**必ずメモしておく**）
   - **Region**: Northeast Asia（Tokyo）を選ぶ
3. 「Create new project」をクリック
4. プロジェクトの初期化に 1〜2 分かかります（待つ）

---

## 3. テーブルを作る

1. 左メニューの「Table Editor」をクリック
2. 「New table」をクリック
3. `mvp/STEP4.md` のデータ設計を参考にテーブルとカラムを設定
   - 例：テーブル名 `items`、カラム `title (text)`, `created_at (timestamptz)`
4. 「Save」をクリック

---

## 4. API キーを取得する

1. 左メニューの「Project Settings」→「API」をクリック
2. 以下の2つの値をコピーして `.env.local` に貼る

```
NEXT_PUBLIC_SUPABASE_URL=https://xxxx.supabase.co
NEXT_PUBLIC_SUPABASE_ANON_KEY=eyJhbGciOi...（長い文字列）
```

> **注意**: この値は外部に公開しないこと。GitHub に push する前に `.gitignore` に `.env.local` が入っているか確認する。

---

## 5. RLS（Row Level Security）の設定

Supabase のテーブルはデフォルトで RLS がオンになっており、設定なしだとデータが取得できません。

**開発中の簡易設定（公開データの場合）**

1. 「Table Editor」→ テーブルを選択 → 「RLS」タブ
2. 「Add policy」→「Enable read access to everyone」を選ぶ
3. 書き込みも必要なら「Enable insert for all users」も追加

> ログイン機能を実装する場合は、ユーザー ID に紐づいたポリシーが必要です。実装時にチャットで相談してください。

---

## 確認

`.env.local` に2つの環境変数が入っていて、テーブルが作れていれば準備完了です。
Step4 の実装に戻ってください。
