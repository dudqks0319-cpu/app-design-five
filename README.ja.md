# App Design Five

[한국어](README.md) · [English](README.en.md) · [简体中文](README.zh-CN.md) · [日本語](README.ja.md)

**アプリを作る前に、実際の画像として生成した UI デザイン案を 5 枚見て選べる AI エージェント向けスキルです。**

画像 5 枚 → 選択・組み合わせ → デザイン制作 → 依頼されたアプリ実装

同じアプリの主要画面について、異なる 5 つのデザイン方向を比較します。「案 1 の構成に案 4 の配色」のように選んだり組み合わせたりした後、OpenDesign の Local Codex モードでデザインを制作します。アプリの実装まで依頼された場合のみ実装に進みます。通常の不具合修正や状況確認では、この流れを開始しません。

## 作業の流れ

1. アプリの目的、プラットフォーム、主要画面、必須機能を整理します。
2. Codex の画像ツールで、レイアウトや情報構成が異なる **5 枚の独立した画像**を生成して表示します。
3. ユーザーが番号を選ぶか、案を組み合わせて修正意見を伝えます。方向が選ばれるまでは次のデザイン制作を開始しません。
4. 選んだ方向で OpenDesign のデザインを制作します。既定の実行モードは **Local Codex** です。
5. 実装まで依頼された場合は、実際の画面と機能に反映します。デザインのみの依頼は、その範囲で終了します。

## スキルと MCP

| 形式 | 役割 | このプロジェクトでの使用 |
| --- | --- | --- |
| スキル | AI に作業手順と判断基準を伝えます。 | `SKILL.md` と参照文書として配布します。 |
| MCP | AI とプログラムのツールやリソースを接続します。 | デザイン段階では既存の OpenDesign 接続を使用します。 |

このリポジトリは **スキルパッケージ**です。独立した MCP サーバー、画像エンジン、OpenDesign アプリ、API キー、生成クレジットは含まれていません。

## 必要な環境

| ホスト | スキル文書 | 画像生成 | デザイン・実装 |
| --- | --- | --- | --- |
| Codex | 共通の Agent Skills 形式 | インストール済みの `imagegen` スキルと内蔵画像ツールが必要 | インストール・認証済みの OpenDesign + Local Codex |
| OpenCode | 同じ `SKILL.md` 形式 | そのホストで利用できる画像ツールが必要。既存の画像案も再利用可能 | 利用可能な OpenDesign 接続、またはユーザーが明示的に選んだ直接実装 |

OpenCode にこのスキルを入れるだけで Codex の画像ツールが接続されるわけではありません。必要なツールがない段階は未完了として伝え、有料 API、Cloud、BYOK には自動で切り替えません。

## インストール

既存の `skills` CLI を使う任意の方法です。Node.js/npm が必要で、外部インストールツールを実行します。

```sh
npx skills add dudqks0319-cpu/app-design-five --skill app-design-five -g -a codex -a opencode
```

別のインストールツールを使わない場合は、リポジトリの ZIP をダウンロードするかクローンした後、**リポジトリのフォルダー内で**次を実行します。同じ名前の既存スキルは上書きしません。

```sh
mkdir -p "$HOME/.agents/skills"
if [ -e "$HOME/.agents/skills/app-design-five" ] || [ -L "$HOME/.agents/skills/app-design-five" ]; then
  echo '同じ名前のスキルがあります。置き換える前に既存の内容を確認してください。'
else
  mkdir "$HOME/.agents/skills/app-design-five" &&
  cp -R SKILL.md LICENSE agents references "$HOME/.agents/skills/app-design-five/"
fi
```

特定のプロジェクトだけで使用する場合は、同じファイルを `.agents/skills/app-design-five/` に置きます。ユーザー単位とプロジェクト単位で同じ名前を重複インストールしないでください。インストール後は現在のホストのスキル一覧で検出を確認します。

## 使用例

```text
$app-design-five を使って家計簿アプリを作ってください。
まず画像のデザイン案を 5 枚見せて、私が選んだら OpenDesign で続けてください。
```

```text
$app-design-five でデザインだけ提案してください。アプリのコードはまだ変更しないでください。
```

```text
案 1 のリスト構成と案 4 の配色を組み合わせてください。文字はもっと大きくしてください。
```

OpenCode で既存の画像案を使う例：

```text
app-design-five スキルを使ってください。既存の画像から案 3 を選びます。
今回は OpenDesign ではなく、現在の OpenCode プロジェクトに実装してください。
```

ユーザーの選択、実行モード、実装・検証の範囲を維持します。このスキル自体は追加エージェント、支払い、デプロイ、GitHub 公開を許可するものではありません。

## 確認済みの範囲と制限

- スキル形式、文書内リンク、ローカルインストールファイルの一致を確認し、Codex のスキルカタログに表示されることも確認しました。
- このスキルを使った「画像 5 枚 → OpenDesign → アプリ実装」の全体の流れは、まだ実行して検証していません。
- OpenCode の実際の動作と外部インストール CLI コマンドも、このプロジェクトではまだ検証していません。
- 画像、デザイン結果、ソース実装、ローカル確認、実機での使用、リリース状況を、それぞれ観測した根拠に基づいて報告します。検証を省略した場合は明示します。

## ファイルとプライバシー

エージェント向けの実行指示は 1 つの英語版 `SKILL.md` に統一し、使用案内は 4 言語で提供します。`agents/openai.yaml` は Codex の UI メタデータ、`references/` はツールの使い分けとデザインの引き継ぎ手順です。

生成画像や個人のブリーフは、対象アプリのローカル作業フォルダーに保存します。`.local/` の記録、個人の画面、認証情報は配布対象から除外します。実行スクリプト、遠隔データ収集、自動更新機能は含まれていません。

## ライセンスと参考

[MIT ライセンス](LICENSE)。ユーザーが紹介した [oil-ui](https://github.com/oil-oil/oil-ui) の複数の方向を比較する考え方を参考にした独立したスキルです。同リポジトリのコード、スキル本文、画像は含めていません。

[Agent Skills 標準](https://agentskills.io/home) · [Codex スキル](https://learn.chatgpt.com/docs/build-skills) · [OpenCode スキル](https://opencode.ai/docs/skills/) · [skills CLI](https://github.com/vercel-labs/skills) · [MCP](https://modelcontextprotocol.io/docs/learn/architecture)
