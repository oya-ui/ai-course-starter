# ai-course-starter

AIコース受講生向けの Cursor スキルセットです。  
このリポジトリをクローンして自分のプロジェクトに置くと、チャットから `/skill名` で呼び出せるようになります。

---

## セットアップ

```bash
git clone https://github.com/oya-ui/ai-course-starter.git
```

クローンしたら、Cursor でこのフォルダを開くか、**自分のプロジェクトの `.cursor/` フォルダに中身をコピー**してください。

---

## スキル一覧

### `business-plan-interview`

事業プランや意思決定メモを対話形式で整理するスキル。  
AIが順番に質問しながら「論点の地図 → 突破順 → 1枚サマリー」まで作ってくれます。

呼び出し方：チャットで `/business-plan-interview` または「事業プラン」「ビジネスプラン」と入力する

---

### `course-mvp-step1-hypothesis`

**MVP Step 1 ── 仮説づくり**

実現難易度（緑/黄/赤）を確認しながら、MVP の仮説ドキュメント `STEP1_MVP_HYPOTHESIS.md` を作成します。

呼び出し方：`/course-mvp-step1-hypothesis` または「Step1」「MVP仮説」

---

### `course-mvp-step2-story-scope`

**MVP Step 2 ── ストーリー & スコープ整理**

Step1 の仮説をもとに、ユーザーストーリー・画面一覧・スコープ（A〜D段階）・MVP チェックリストをまとめた `STEP2_STORY_SCENARIO.md` を作成します。

呼び出し方：`/course-mvp-step2-story-scope` または「Step2」「ストーリー」「スコープ」

---

### `course-mvp-step3-ui-mock`

**MVP Step 3 ── UI モック作成 & フィードバックループ**

Step2 のストーリーをもとに `STEP3_UI_MOCK.html` を生成し、フィードバック → 改善を繰り返します。OKが出るまで対話形式で磨きます。

呼び出し方：`/course-mvp-step3-ui-mock` または「Step3」「モック」「フィードバック」

---

### `course-mvp-step4-implement-host`

**MVP Step 4 ── 実装 & デプロイ**

Step3 のモック承認後、`STEP4_IMPLEMENTATION_PLAN.md` を作成し、Next.js + Supabase で実装、Vercel にデプロイするまで伴走します。初心者向けに npm install から順に進めます。

呼び出し方：`/course-mvp-step4-implement-host` または「Step4」「実装」「デプロイ」

---

## ステップの流れ

```
Step1: 仮説づくり
  ↓
Step2: ストーリー & スコープ整理
  ↓
Step3: UI モック作成（フィードバックループ）
  ↓
Step4: 実装 & Vercel デプロイ
```

---

## 注意

- `.cursor/skills/` と `.cursor/rules/` の中身が機能します。Cursor 以外のエディタでは動きません。
- スキルは Cursor のチャット欄から `/スキル名` で呼び出してください。
