# Skills入門 — 公開Skill「Cognitive View」再現チートシート

対象: 普段AIを使っているビジネス職・企画職・AI推進担当 / 所要: 10〜15 分 / 最終確認: 2026-09-23（リンクと固定commitの中身を開催前に確認）

当日の「公開OSSのSkillを、自分が普段使っているAIにリンクで渡して1回実行する（USE）」を、そのままたどる手順です。AIが出した結果の確認と、その利用の判断は試す人が持ちます。

## 前提

- 道具: **普段お使いのAIで構いません**（ChatGPT / Microsoft Copilot / Gemini / Claude / Codex / Claude Code 等）。新しいアカウントや環境構築は不要です
- 型: 公開OSS `yamamonlab/biz-terrace-ai-skills` の `skills/cognitive-view/`。当日は commit `78ce777a1ad8423dce2eb00757f0149021349ccb` に固定して使いました
- データ: **公開資料かダミーデータだけ**を使ってください。業務データ、顧客情報、個人情報は入れない
- このSkillの用途: **自分が受け取った長文を理解するための道具**です。提出物・配布物を作る型ではありません

## 手順

### 1. 型を読める状態にする

Cognitive View は `SKILL.md` だけではなく `references/` を含めて1つのSkillです。**SKILL.md だけを渡した状態は完全な実行ではありません。**

**フォルダごと読める環境**（Codex / Claude Code / リポジトリ連携）は、このURLをそのまま渡します。

```text
https://github.com/yamamonlab/biz-terrace-ai-skills/tree/78ce777a1ad8423dce2eb00757f0149021349ccb/skills/cognitive-view
```

**チャットAI**（ChatGPT / Copilot / Gemini / Claude 等）は、**フォルダのURLを渡してもファイル一覧しか見えません。** 中身は1URL＝1ファイルなので、次の4本をまとめて貼り、「このリンクを全部読んでから作業して」と添えます。

```text
https://raw.githubusercontent.com/yamamonlab/biz-terrace-ai-skills/78ce777a1ad8423dce2eb00757f0149021349ccb/skills/cognitive-view/SKILL.md
https://raw.githubusercontent.com/yamamonlab/biz-terrace-ai-skills/78ce777a1ad8423dce2eb00757f0149021349ccb/skills/cognitive-view/references/output-contract.md
https://raw.githubusercontent.com/yamamonlab/biz-terrace-ai-skills/78ce777a1ad8423dce2eb00757f0149021349ccb/skills/cognitive-view/references/quality-rubric.md
https://raw.githubusercontent.com/yamamonlab/biz-terrace-ai-skills/78ce777a1ad8423dce2eb00757f0149021349ccb/skills/cognitive-view/references/capability-spec.md
```

図（SVG）まで描かせたい場合は、`references/diagram/grammar.md` と、描かせたい型の `references/diagram/type-*.md`（timeline / flowchart / process / state / quadrant / tree / bar）を同じ形式で追加します。

社内ポリシーで外部リンクの取得が止まっている場合は、同じURLをブラウザで開いて本文をコピーし、チャットへ貼っても同じです（`SKILL.md` は約2万字あるので分割して貼ることになります）。

### 2. 資料を渡す

まずは公開サンプル（社内AIツール導入検討の架空メモ）で試すのが確実です。

```text
https://raw.githubusercontent.com/yamamonlab/biz-terrace-ai-skills/78ce777a1ad8423dce2eb00757f0149021349ccb/skills/cognitive-view/examples/sample-document.md
```

### 3. 1行だけ依頼する

```text
この資料を、短時間で全体像を把握できる Cognitive View にしてください。HTMLで出力してください。
```

## 確認ポイント

正解のレイアウトを当てるものではありません。次が満たされているかを見ます。

- 先頭だけで「何の資料で、今どういう状態か」が分かる
- 原文に重要数値がある場合**だけ**メトリクスが出る（数値がないのにカードを作っていない）
- 比較は表、時系列は日付リストか図、というように関係に合う表現が選ばれている
- 推測・未確認が事実と混ざっていない
- **原文にない優先順位や推奨が足されていない**（既定は理解支援のみ。判断材料が欲しい時だけ「比較して判断材料をください」と追加で頼む）
- 詳細は後ろへ折りたたまれている

モデルによって文章や配置の細部は変わります。狙いは完全一致ではなく、同じ判断基準と骨格へ寄せることです。

完成形の例: https://biz-terrace-ai.pages.dev/handson/2026-09-29/cognitive-view.html

## つまずきどころ

| 症状 | 原因 | 対処 |
|---|---|---|
| 普通の要約文が返る | 型が読めていない | `references/` まで渡したか確認する。チャットAIならコピー用リンク（raw リンク）4本方式へ切り替える |
| AIが「読めません」と言う | フォルダURLを渡している／外部取得が止まっている | コピー用リンク（raw リンク）方式、それでも駄目なら本文コピー貼り付けへ |
| HTMLがコードのまま表示される | プレビュー表示になっていない | チャット内のプレビュー（アーティファクト）表示へ切り替える。難しければ上の完成形URLを開く |
| 無料枠の上限で止まる | メッセージ制限 | 上の完成形URLで結果を確認し、後で自分の環境でやり直す |

## 次の一歩

1. **USE（借りる）** — 今日やったこと。公開されている型をそのまま使う
2. **TUNE（直す）** — 同じSkillの `Audience` を「経営層向け」などに変え、初期表示の焦点だけを変える。情報は消さない
3. **MAKE（作る）** — 普段のチャットで良い仕事ができた直後に「今の作業を、別の仕事でも再現できるように SKILL.md にして」と頼む。「具体的な社名や数値などの固有名詞は抜いて汎用的にして」と添えると、過学習を防げる
