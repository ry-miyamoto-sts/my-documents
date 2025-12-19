# 画像フォルダ

このフォルダに、Geminiで生成した画像を配置してください。

## 必要な画像（10枚）

1. `title-architecture.png` - タイトル用
2. `architecture-blueprint.png` - アーキテクチャの説明用
3. `bad-vs-good-code.png` - 悪いコード vs 良いコードの比較
4. `spaghetti-code.png` - スパゲッティコードの表現
5. `layered-architecture.png` - レイヤードアーキテクチャの図
6. `mvc-pattern.png` - MVCパターンの図
7. `dry-principle.png` - DRY原則の説明用
8. `refactoring.png` - リファクタリングの表現
9. `team-development.png` - チーム開発の様子
10. `success-celebration.png` - 成功のお祝い

## 画像生成方法

1. `gemini-image-prompts.txt` を開く
2. 各プロンプトをGeminiにコピー＆ペースト
3. 生成された画像を対応するファイル名で保存
4. このフォルダに配置

## 推奨サイズ

- 横: 1200px、縦: 675px（16:9）
- または 800x450px

## 生成後

画像を配置したら、以下のコマンドでプレゼンテーションを再生成：

```bash
npm run build
```
