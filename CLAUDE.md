# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Purpose

Documents repository for Marp presentations. Currently contains `src/architecture-presentation.md` - a 12-15 minute Lightning Talk on "What is a Good System?" targeted at web application developers who are focused on task completion rather than system quality.

### Presentation Philosophy
- **Audience**: Web developers who just do tasks assigned by leaders, without thinking about good system design
- **Goal**: Inspire curiosity about architecture - make them want to learn more on their own (not to teach everything)
- **Approach**:
  - Start with business/management perspective (not just technical)
  - Use smartphone home screen as relatable analogy for code organization
  - Show just enough to spark interest, not complete solutions
  - End with "this is the world of architecture - it's deep and interesting!"
  - Liberal use of emojis for friendly, casual tone

## Build Commands

All generated files output to `dist/` directory (gitignored).

```bash
# Generate all formats (HTML, PDF, PowerPoint)
npm run build:all

# Individual formats
npm run build        # HTML + images sync (rsync for efficiency)
npm run build:pdf    # PDF (requires Chromium + Japanese fonts)
npm run build:pptx   # PowerPoint (requires Chromium + Japanese fonts)

# Development
npm run preview      # Live preview server at localhost:8080
```

**Important**: `npm run build` uses rsync to copy images incrementally. Only changed files are copied to `dist/images/`.

## Environment Setup

### WSL/Linux (First-time setup)
```bash
# Install Chromium browser
sudo apt-get update && sudo apt-get install -y chromium-browser

# Install Japanese fonts (critical for PDF/PPTX)
sudo apt-get install -y fonts-noto-cjk fonts-noto-cjk-extra

# Update font cache
fc-cache -fv
```

**Without Japanese fonts**: PDF/PPTX will show □ (tofu) instead of Japanese text.

### macOS/Windows
Japanese fonts pre-installed. Only need Chrome/Edge/Firefox for PDF/PPTX generation.

## File Structure

```
src/
  architecture-presentation.md  # Marp presentation source (16 slides)
  images/                        # Presentation images
    title-design-visual.png      # Title slide background
    ai-icons.png                 # AI services icons
    software-design-basics.png   # Design fundamentals diagram
dist/                            # Generated files (gitignored)
  *.html, *.pdf, *.pptx
  images/                        # Copied from src/images/ during build
発表原稿.md                       # Presentation script with timing notes (gitignored)
```

## Marp File Format

- YAML frontmatter: `marp: true`, `theme`, `paginate`, `style` (for fonts)
- Slides separated by `---`
- Images: `![bg right:40%](images/filename.png)` for background placement (relative to .md file)
- Font specification in frontmatter prevents Japanese text issues in PPTX

### Current Presentation Structure (16 slides)

1. **Title slide** - `![bg right:45%](images/title-design-visual.png)` - 縦長画像（3:2）
2. **なぜ今、このテーマなのか？** - `![w:800](images/ai-icons.png)`
3. **では、エンジニアに求められるものは？** 🎓
4. **理想のシステム像** 🎯
5. **設計原理：CLEAN** 💡 - SOLID原則との紐づけ（右寄せ）
6. **ソフトウェア設計の基本** 🔧 - `![w:1000](images/software-design-basics.png)`
7. **なぜ分けるのか？** 💡
8. **良くないコードの例（C#）** 🤖 - 5つの関心が混在
9. **何が問題か？** 🔍
10. **関心が分離されていないと...** 💥 - 開発者の痛み（チーム開発、変更の恐怖、開発速度）
11. **リファクタリング例①：関心の分離** ✨
12. **リファクタリング例②：サービスの組み合わせ** ✨
13. **明日からできること** 💪 - 2つの習慣（自分に問いかける、AIに問いただす）
14. **もっと深く学ぶには** 📚 - 米久保氏の資料
15. **まとめ** 📝
16. **ちなみに、この資料は...** 📊 - Marp, Claude Code, Geminiの紹介

**Key flow**: Slides 5-7 順序重要 - 「今日は関心の分離をやります」→「設計の基本は分けることです」が自然な流れ

### Presentation Design Principles
- **No spoilers in titles**: Don't reveal answers in slide titles - use questions instead to create curiosity
- **Interactive moments**: Include slides with just questions and `(ちょっと考えてみて)` to let audience think
- **Smartphone analogy**: Core teaching device - messy vs organized home screen maps to messy vs organized code
- **Show hints, not complete solutions**: Give glimpses of good architecture to make them curious, not everything
- **Target 12 minutes**: Aim for ~1 minute per slide, 12-18 slides total

## CLEAN to SOLID Mapping

Reference source: https://www.docswell.com/s/tyonekubo/5R2Y4E-architecture2design#p44

- **C (Cohesive - 高凝集)** → 単一責任原則 (SRP)
- **L (Loosely Coupled - 疎結合)** → インターフェース分離原則 (ISP)
- **E (Encapsulated - カプセル化)** → オープン・クローズドの原則 (OCP)、依存性逆転原則 (DIP)
- **A (Assertive - 関心の分離)** → 単一責任原則 (SRP)、インターフェース分離原則 (ISP)
- **N (Nonredundant - 非冗長)** → DRY原則、YAGNI原則

**Important**: One CLEAN principle can map to multiple SOLID principles.

### CLEAN Grid Layout (Slide 5)

3-column layout:
```
[Letter] [Name + Japanese (centered)] [SOLID principles (right-aligned)]
```

CSS structure:
- `.clean-letter`: 32px, gold (#ffd700), 45px width, center-aligned
- `.clean-item strong`: 26px, center-aligned (e.g., "Cohesive（高凝集）")
- `.clean-item small`: 20px, right-aligned, #ffeb3b color (e.g., "単一責任原則 (SRP)")

## Key Content Changes from Previous Versions

1. **Slides 13-14 deleted**: 原理→原則→実装の理論的な話は削除（小難しいため）
2. **Slide 10 rewrite**: "1つの変更がすべてに影響" → 開発者の痛み（チーム開発困難、変更が怖い、開発速度低下）
3. **Slide 13 simplification**:
   - Before: 4つの抽象的なアクションアイテム
   - After: 2つの習慣（「この処理、本当にここに書くべき？」+ AIに原則名で問いただす）
4. **Image updates**:
   - Deleted: image2.png, image3.png (unused)
   - Renamed: image4.png → title-design-visual.png, image1.png → software-design-basics.png
   - Current: title-design-visual.png (right:45%), ai-icons.png (800px), software-design-basics.png (1000px)

## Code Example Standards

**Language**: C# (ASP.NET MVC)

**Bad example** (Slide 8): UserController.Register()
- 5つの関心が混在：バリデーション、DB接続・操作、ビジネスロジック、メール送信、Slack通知
- SQLインジェクション脆弱性も含む（教育目的）

**Good example** (Slides 11-12): 関心ごとに分離
- UserRepository - DB操作のみ
- UserValidator - 検証のみ
- EmailService - メール送信のみ
- NotificationService - 通知のみ
- Controller - 各サービスを組み合わせるだけ

**Key message**: "変更の影響が局所化された！" ✅

## Styling Guidelines

### Color Scheme
- **Background**: Purple gradient (#667eea → #764ba2)
- **Accent**: Gold (#ffd700)
- **Text**: White on gradient background
- **Code blocks**: Dark (#1e1e1e) with syntax highlighting

### Typography
- **Font**: 'Noto Sans CJK JP', 'Noto Sans JP' (日本語対応)
- **H1**: 60px, gold, text-shadow, border-bottom
- **H2**: 48px, gold, border-left 8px
- **Body**: 28px, line-height 1.6
- **Code**: 0.58em (最小限、これ以上小さくすると読めない), line-height 1.3

### Layout Constraints
- **上詰めレイアウト**: `justify-content: flex-start` (タイトルスライド以外)
- **CLEAN grid spacing**: `gap: 0.25em`, `padding: 0.3em 1.2em` (最適化済み、これ以上縮めると読めない)
- **Code block padding**: `0.5em 0.6em` (最小限に最適化済み)

### Common Pitfalls to Avoid
- **Do not use table/flex/grid for layout**: Creates white background issues that break the purple gradient
- **Do not increase CLEAN grid spacing**: Already optimized for screen fit
- **Do not change code block font size**: Current 0.58em is minimum readable size
- **For 2-column layouts**: Use simple stacking instead of complex layouts

## Image Workflow

All required images are already in place:
- `title-design-visual.png` - Title slide background (right:45%)
- `ai-icons.png` - AI services icons (800px width)
- `software-design-basics.png` - Design fundamentals diagram (1000px width)

If you need to add or replace images:
1. Generate images with Gemini or other AI tools
2. Save to `src/images/` folder
3. Update image references in `src/architecture-presentation.md`
4. Rebuild: `npm run build:all`

### Image Specifications
- **Size**: 1200x675 (16:9) recommended
- **Colors**: Purple (#667eea-#764ba2), Gold (#ffd700)
- **Style**: Modern flat illustration, professional
- **Text**: NO TEXT in images (icons only)

## Git Workflow

- Main branch: `main`
- Feature branches: `feature/[description]`
- Images gitignored by default - explicitly unignore to track
- `dist/` completely gitignored
