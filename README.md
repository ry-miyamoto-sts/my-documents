# my-documents

ドキュメントと発表資料を管理するリポジトリ

## コンテンツ

- `src/architecture-presentation.md` - AI時代の設計入門（Marp形式、16スライド、12-15分想定）
  - 対象：AI時代のエンジニア向け
  - テーマ：良い設計とは何か（関心の分離・CLEAN原則）
  - AIが生成したコードの評価方法
  - 具体例：C#のユーザー登録処理のリファクタリング
  - 実践：明日からできる2つの習慣

## セットアップ

### 前提条件

- Node.js（npmコマンドが使える環境）

### 1. PDF/PowerPoint生成のためのブラウザインストール

PDF・PowerPoint形式の生成には、ブラウザ（Chromium）が必要です。

#### WSL/Linux環境の場合

```bash
sudo apt-get update
sudo apt-get install -y chromium-browser
```

インストール確認：
```bash
chromium-browser --version
```

#### macOS環境の場合

Homebrewを使用：
```bash
brew install --cask chromium
```

#### Windows環境の場合

Chrome、Edge、またはFirefoxをインストール済みであれば追加作業は不要です。

### 2. 日本語フォントのインストール

PDF・PowerPoint形式で日本語を正しく表示するために、日本語フォントが必要です。

#### WSL/Linux環境の場合

```bash
sudo apt-get update
sudo apt-get install -y fonts-noto-cjk fonts-noto-cjk-extra
```

インストール確認：
```bash
fc-list :lang=ja | head -5
```

フォントキャッシュ更新：
```bash
fc-cache -fv
```

**注意**: フォントをインストールせずにPDF/PowerPointを生成すると、日本語が□（豆腐）で表示されます

#### macOS/Windows環境の場合

日本語フォントが標準でインストールされているため、追加作業は不要です。

## Marp資料の生成

### HTML形式で生成（推奨）
```bash
npm run build
```

生成物: `dist/architecture-presentation.html`

### PDF形式で生成（要ブラウザ）
```bash
npm run build:pdf
```

生成物: `dist/architecture-presentation.pdf`

### PowerPoint形式で生成（要ブラウザ）
```bash
npm run build:pptx
```

生成物: `dist/architecture-presentation.pptx`

### 全形式で生成
```bash
npm run build:all
```

### プレビューサーバーを起動
```bash
npm run preview
```
ブラウザで http://localhost:8080 にアクセス

## 出力先

- `dist/architecture-presentation.*` （HTML/PDF/PPTX）
- `dist/images/` （画像ファイル）

**注意**: 生成されたファイル（dist/ディレクトリ）はGit管理対象外です

## 画像の生成と管理

プレゼンテーションには3枚の画像を使用しています。画像は全てAI（Gemini）で生成しました。

### 使用中の画像

1. **title-design-visual.png** - タイトルスライド背景（右側45%）
   - 縦長画像（3:2アスペクト比）
   - 設計の視覚的イメージ

2. **ai-icons.png** - AI時代のエンジニア（スライド2）
   - 横長画像（800px幅）
   - GitHub Copilot、Cursor、ChatGPT、Claude、Devin、Geminiのアイコン

3. **software-design-basics.png** - ソフトウェア設計の基本（スライド6）
   - 横長画像（1000px幅）
   - 設計の基本概念を視覚化

### 新しい画像の追加

追加の画像が必要な場合：

1. **GeminiやChatGPTで画像を生成**
2. **画像を保存して反映**
   ```bash
   # src/images/ フォルダに保存
   mv ~/Downloads/生成画像.png src/images/新しい画像.png

   # src/architecture-presentation.md で画像を参照

   # プレゼンテーションを再生成
   npm run build:all
   ```

### 画像の仕様

- **サイズ**: 1200px × 675px (16:9)
- **カラー**: パープル系 (#667eea - #764ba2) + ゴールド (#ffd700)
- **スタイル**: モダンフラットイラスト、プロフェッショナル
- **テキスト**: 画像内に文字を入れない（アイコンのみOK）

## ファイル構成

```
my-documents/
├── src/
│   ├── architecture-presentation.md    # Marpプレゼンテーション（16スライド）
│   └── images/                         # プレゼンテーション用画像
│       ├── title-design-visual.png     # タイトル背景画像
│       ├── ai-icons.png                # AIサービスアイコン
│       └── software-design-basics.png  # 設計基本図
├── dist/                               # 生成ファイル（gitignore）
│   ├── architecture-presentation.html  # HTMLプレゼンテーション
│   ├── architecture-presentation.pdf   # PDF版
│   ├── architecture-presentation.pptx  # PowerPoint版
│   └── images/                         # 画像（src/imagesからコピー）
├── 発表原稿.md                          # 発表台本（gitignore、個人メモ）
├── package.json                        # npm設定
├── README.md                           # このファイル
└── CLAUDE.md                           # Claude Code用ガイド
```

## トラブルシューティング

### PDF/PowerPointで日本語が文字化けする

**原因**: 日本語フォントがインストールされていない

**解決方法**:
```bash
# Linux/WSL
sudo apt-get install -y fonts-noto-cjk fonts-noto-cjk-extra
fc-cache -fv

# macOS/Windows: 標準でインストール済み
```

### ビルドエラー: "Chromium not found"

**原因**: Chromiumブラウザがインストールされていない

**解決方法**:
```bash
# Linux/WSL
sudo apt-get install -y chromium-browser

# macOS
brew install --cask chromium

# Windows
Chrome、Edge、Firefoxのいずれかをインストール
```

### 画像が表示されない

**原因**: 画像ファイルが存在しないか、ファイル名が間違っている

**解決方法**:
1. `src/images/` に画像が存在するか確認
2. ファイル名が正確に一致しているか確認（大文字小文字を区別）
3. `npm run build` を実行して画像を同期

### コードが画面に収まらない

**現在の設定**: フォントサイズとパディングは既に最小限に最適化済み

**対処方法**:
1. コード例を短縮する（冗長な部分を削除）
2. 変数名を短くする
3. 複数スライドに分割する

## 開発の流れ

### プレゼンテーション内容の編集

1. `src/architecture-presentation.md` を編集
2. プレビューで確認: `npm run preview`
3. ブラウザで http://localhost:8080 を開く
4. 変更を保存すると自動でリロード

### 画像の追加・変更

1. GeminiやChatGPTで新しい画像を生成
2. `src/images/` に保存
3. `src/architecture-presentation.md` で画像を参照
4. `npm run build` で反映

### スタイルの調整

1. `src/architecture-presentation.md` のYAML frontmatterの `style:` セクションを編集
2. プレビューで確認
3. 変更を保存

**注意**:
- CLEAN grid の縦幅は既に最適化済み（これ以上縮めると読めない）
- コードブロックのフォントサイズは最小限（0.58em）

## 技術スタック

- **Marp**: Markdownからプレゼンテーションを生成
- **Marp CLI**: コマンドラインでのビルドツール
- **rsync**: 画像の効率的な同期
- **Chromium**: PDF/PPTX生成用のヘッドレスブラウザ

## ライセンス

このプロジェクトは社内用LT資料です。
