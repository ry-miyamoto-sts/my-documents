# my-documents

ドキュメントと発表資料を管理するリポジトリ

## コンテンツ

- `src/architecture-presentation.md` - アーキテクチャ入門のLT資料（Marp形式）

## セットアップ

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

**注意**: フォントをインストールせずにPDF/PowerPointを生成すると、日本語が□（豆腐）で表示されます

#### macOS環境の場合

macOSには日本語フォントが標準でインストールされているため、追加作業は不要です。

#### Windows環境の場合

Windowsには日本語フォントが標準でインストールされているため、追加作業は不要です。

### 3. その他のブラウザ（macOS/Windows）

#### macOS環境の場合

Homebrewを使用：
```bash
brew install --cask chromium
```

#### Windows環境の場合

Chrome、Edge、またはFirefoxをインストール済みであれば追加作業は不要です。

## Marp資料の生成

### HTML形式で生成（推奨）
```bash
npm run build
```

### PDF形式で生成（要ブラウザ: Chrome/Edge/Firefox）
```bash
npm run build:pdf
```

### PowerPoint形式で生成（要ブラウザ: Chrome/Edge/Firefox）
```bash
npm run build:pptx
```

### 全形式で生成
```bash
npm run build:all
```

### プレビューサーバーを起動
```bash
npm run preview
```
ブラウザで http://localhost:8080 にアクセス

## 注意事項

- 生成されたファイル（dist/ディレクトリ）はGit管理対象外です
- PDF・PPTX形式の生成には、上記「セットアップ」で説明したブラウザのインストールが必要です
- HTML形式のみであれば、ブラウザのインストールなしで生成可能です

## 画像の差し替え

プレゼンテーションの挿絵を変更する場合：

1. `src/images/gemini-image-prompts.txt` のプロンプトをGeminiで実行
2. 生成された画像を `src/images/` フォルダに保存（既存ファイルを上書き）
3. `npm run build:all` で再生成