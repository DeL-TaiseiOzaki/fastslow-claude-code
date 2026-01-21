# fastslow-claude-code

Claude Code (Fast/System 1) と Codex CLI (Slow/System 2) の設定を既存プロジェクトに導入するスターターキット。

## 導入方法

```bash
# 1. 既存プロジェクトのルートで実行
git clone --depth 1 https://github.com/DeL-TaiseiOzaki/fastslow-claude-code.git .starter

# 2. 必要なファイルをコピー
cp -r .starter/.claude .starter/.codex .starter/AGENTS.md .
cp -P .starter/CLAUDE.md .

# 3. クリーンアップ
rm -rf .starter

# 4. プロジェクトを初期化
claude  # Claude Code を起動
/init   # AGENTS.md をプロジェクトに合わせて更新
```

**ワンライナー:**
```bash
git clone --depth 1 https://github.com/DeL-TaiseiOzaki/fastslow-claude-code.git .starter && cp -r .starter/.claude .starter/.codex .starter/AGENTS.md . && cp -P .starter/CLAUDE.md . && rm -rf .starter
```

## Codex CLI のグローバル設定（初回のみ）

Codex CLI が `.claude/` のコンテキストを読み込むために、以下の設定が必要です:

```bash
# 1. Codex 用グローバル指示をコピー
cp .codex/AGENTS.md ~/.codex/AGENTS.md

# 2. スキル機能を有効化（未設定の場合）
cat >> ~/.codex/config.toml << 'EOF'
[features]
skills = true
EOF
```

## 構成

```
.claude/          # Claude Code 設定
├── agents/       # サブエージェント（自動委譲）
├── commands/     # コマンド（/init, /plan, /tdd 等）
├── skills/       # スキル（自動発動）
├── rules/        # 常時適用ルール
├── docs/         # 知識ベース
└── settings.json # 権限設定

.codex/           # Codex CLI 設定
├── AGENTS.md     # グローバル指示（~/.codex/ へコピー）
├── config.toml   # 機能設定
└── skills/       # スキル
    └── context-loader/  # .claude/ コンテキスト読み込み

AGENTS.md         # プロジェクト設定（両ツール共通）
CLAUDE.md         # AGENTS.md へのシンボリックリンク
```

## ライセンス

MIT
