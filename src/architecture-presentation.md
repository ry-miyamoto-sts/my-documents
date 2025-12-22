---
marp: true
theme: default
paginate: true
style: |
  /* ===== 基本設定 ===== */
  section {
    font-family: 'Noto Sans CJK JP', 'Noto Sans JP', sans-serif;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
    font-size: 28px;
    padding: 60px 80px;
    justify-content: flex-start;  /* 上詰めレイアウト */
  }

  /* ===== 表紙スライド（中央配置） ===== */
  section.title {
    justify-content: center;
    text-align: center;
  }

  /* ===== 見出しスタイル ===== */
  h1 {
    font-size: 60px;
    font-weight: 900;
    color: #ffd700;
    text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
    border-bottom: 4px solid #ffd700;
    padding-bottom: 0.3em;
    margin-bottom: 0.5em;
  }

  h2 {
    font-size: 48px;
    font-weight: 700;
    color: #ffd700;
    border-left: 8px solid #ffd700;
    padding-left: 0.5em;
    margin-top: 0;
    margin-bottom: 0.8em;
  }

  h3 {
    font-size: 36px;
    font-weight: 600;
    color: #ffeb3b;
    margin-bottom: 0.6em;
  }

  /* ===== 強調テキスト ===== */
  strong {
    color: #ffd700;
    font-weight: bold;
  }

  /* ===== リンク ===== */
  a {
    color: #ffd700;
    text-decoration: underline;
  }

  a:hover {
    color: #ffeb3b;
    text-decoration: underline;
  }

  /* ===== リスト ===== */
  ul, ol {
    margin-left: 1em;
  }

  li {
    margin-bottom: 0.4em;
    line-height: 1.6;
  }

  /* ===== コードブロック ===== */
  pre {
    background: #1e1e1e;
    border-radius: 8px;
    padding: 0.5em 0.6em;
    font-size: 0.58em;
    line-height: 1.3;
    box-shadow: 0 4px 6px rgba(0,0,0,0.3);
  }

  code {
    background: #2d2d2d;
    color: #d4d4d4 !important;
    font-family: 'Consolas', 'Monaco', monospace;
  }

  /* コードブロック内のすべてのテキストを明るく */
  pre code,
  pre code * {
    color: #d4d4d4 !important;
  }

  :not(pre) > code {
    background: rgba(255,255,255,0.2);
    padding: 0.2em 0.4em;
    border-radius: 4px;
    font-size: 0.9em;
  }

  /* ===== シンタックスハイライトのカスタマイズ ===== */
  /* 文字列リテラル（すべてのタイプ） */
  .hljs-string,
  .hljs-attr,
  .hljs-template-variable,
  .hljs-quote,
  code .hljs-string,
  pre code .hljs-string {
    color: #a8e6cf !important;  /* 優しいミントグリーン */
  }

  /* 数値 */
  .hljs-number {
    color: #ffd93d !important;  /* 明るいゴールド */
  }

  /* キーワード */
  .hljs-keyword {
    color: #ff6b9d !important;  /* ピンク */
  }

  /* クラス名・型名 */
  .hljs-title, .hljs-class .hljs-title {
    color: #4ecdc4 !important;  /* ターコイズ */
  }

  /* コメント */
  .hljs-comment {
    color: #95a5a6 !important;  /* グレー */
    font-style: italic;
  }

  /* 関数名 */
  .hljs-function .hljs-title {
    color: #ffd93d !important;  /* ゴールド */
  }

  /* 変数名 */
  .hljs-variable, .hljs-params {
    color: #e0e0e0 !important;  /* 明るいグレー */
  }

  /* 演算子 */
  .hljs-operator {
    color: #ff6b9d !important;  /* ピンク */
  }

  /* ===== 白背景スライド用 ===== */
  section.white {
    background: white;
    color: #333;
  }

  section.white h1, section.white h2, section.white h3 {
    color: #667eea;
  }

  section.white h1 {
    border-bottom-color: #667eea;
  }

  section.white h2 {
    border-left-color: #667eea;
  }

  section.white strong {
    color: #667eea;
  }

  /* ===== ボックススタイル ===== */
  .box {
    background: rgba(255,255,255,0.1);
    border-left: 6px solid #ffd700;
    padding: 1em 1.5em;
    margin: 1em 0;
    border-radius: 4px;
  }

  /* ===== アイコンボックス ===== */
  .icon-box {
    padding: 1.5em;
    border-radius: 12px;
    margin: 0.8em 0;
    font-size: 1.1em;
  }

  .icon-box.good {
    background: rgba(76, 175, 80, 0.2);
    border: 3px solid #4caf50;
  }

  .icon-box.bad {
    background: rgba(244, 67, 54, 0.2);
    border: 3px solid #f44336;
  }

  /* ===== 小さいテキスト ===== */
  .small {
    font-size: 0.75em;
    opacity: 0.9;
  }

  /* ===== 大きなテキスト ===== */
  .big {
    font-size: 48px;
    font-weight: bold;
    text-align: center;
    margin: 1em 0;
  }

  /* ===== 2カラムレイアウト ===== */
  .columns {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 2em;
  }

  /* ===== CLEANリスト（縦並び） ===== */
  .clean-grid {
    display: flex;
    flex-direction: column;
    gap: 0.25em;
    margin-top: 0.5em;
  }

  .clean-item {
    background: rgba(255,255,255,0.1);
    padding: 0.3em 1.2em;
    border-radius: 6px;
    border: 2px solid rgba(255,215,0,0.3);
    display: flex;
    align-items: center;
    gap: 1.2em;
  }

  .clean-letter {
    font-size: 32px;
    font-weight: 900;
    color: #ffd700;
    flex-shrink: 0;
    width: 45px;
    text-align: center;
  }

  .clean-item strong {
    font-size: 26px;
    flex: 0 0 auto;
    text-align: center;
  }

  .clean-item small {
    font-size: 20px;
    opacity: 0.9;
    flex: 1;
    text-align: right;
    color: #ffeb3b;
  }
---

<!-- _class: title -->

![bg right:45%](images/title-design-visual.png)

# 良い設計とは

---

## なぜ今、このテーマなのか？ 🤖

**AIがコードを書く時代が来ている**

![w:800](images/ai-icons.png)

---

## では、エンジニアに求められるものは？ 🎓

- AIの力を引き出す指示能力
- AIの出力を評価・判断する能力

**👉「良い設計」の理解が必須**

---

## 理想のシステム像 🎯

1. ビジネス要求を満たせる
2. 変更しやすい
3. チームで開発できる

**👉これらを実現するのが「設計」**

---

## 設計原理：CLEAN 💡

<div class="clean-grid">

<div class="clean-item">
<span class="clean-letter">C</span>
<strong>Cohesive（高凝集）</strong>
<small>単一責任原則 (SRP)</small>
</div>

<div class="clean-item">
<span class="clean-letter">L</span>
<strong>Loosely Coupled（疎結合）</strong>
<small>インターフェース分離原則 (ISP)</small>
</div>

<div class="clean-item">
<span class="clean-letter">E</span>
<strong>Encapsulated（カプセル化）</strong>
<small>オープン・クローズドの原則 (OCP)、依存性逆転原則 (DIP)</small>
</div>

<div class="clean-item">
<span class="clean-letter">A</span>
<strong>Assertive（関心の分離）</strong>
<small>単一責任原則 (SRP)、インターフェース分離原則 (ISP)</small>
</div>

<div class="clean-item">
<span class="clean-letter">N</span>
<strong>Nonredundant（非冗長）</strong>
<small>DRY原則、YAGNI原則</small>
</div>

</div>

<div class="small">

出典: 『レガシーコードからの脱却』David Scott Bernstein 著

</div>

**今日は「関心の分離（A）」を深掘りします**

---

## ソフトウェア設計の基本 🔧

![w:1000](images/software-design-basics.png)

---

## なぜ分けるのか？ 💡

分割によって得られるもの

✅ わかりやすい

✅ テストしやすい

✅ 拡張しやすい

✅ 再利用しやすい

**分割することで、振る舞い以上の力を得る**

---

## 良くないコードの例（C#） 🤖

```csharp
// ユーザー登録機能の実装例
public class UserController : Controller {
  public IActionResult Register(string email, string password, string name) {
    // バリデーション
    if (string.IsNullOrEmpty(email) || !email.Contains("@"))
      return View("Error");

    // DB接続
    var conn = new SqlConnection("Server=localhost;...");
    conn.Open();

    // 重複チェック（SQLインジェクション脆弱性あり）
    var cmd = new SqlCommand($"SELECT COUNT(*) FROM Users WHERE Email='{email}'", conn);
    if ((int)cmd.ExecuteScalar() > 0) return View("Error");

    // パスワードハッシュ化＋ユーザー登録
    var hashed = BCrypt.HashPassword(password);
    new SqlCommand($"INSERT INTO Users VALUES ('{email}', '{hashed}', '{name}')", conn).ExecuteNonQuery();

    // ウェルカムメール＋Slack通知
    new SmtpClient("smtp.example.com").Send(new MailMessage("no-reply", email, "登録完了"));
    new WebClient().UploadString("https://hooks.slack.com/...", $"新規: {email}");

    conn.Close();
    return RedirectToAction("Index");
  }
}
```

**あなたは、このコードをマージしますか？**

---

## 何が問題か？ 🔍

このコードには **5つの異なる関心** が混在している

1. ✅ **バリデーション**
2. 🗄️ **データベース接続・操作**
3. 🔐 **ビジネスロジック**（重複チェック・パスワードハッシュ化）
4. 📧 **メール送信**
5. 📢 **Slack通知**

---

## 関心が分離されていないと... 💥

❌ **チームで開発できない**
作業分担が困難、コンフリクト頻発

❌ **変更が怖い**
影響範囲が予測できない

❌ **開発速度が落ちる**
小さな修正にも大きなコスト

**→ 開発者の認知負荷が高い 🤯**

---

## リファクタリング例①：関心の分離 ✨

```csharp
// データベース操作の関心
public class UserRepository {
  public bool EmailExists(string email) { /* DB操作のみ */ }
  public void CreateUser(User user) { /* DB操作のみ */ }
}

// バリデーションの関心
public class UserValidator {
  public ValidationResult Validate(UserInput input) { /* 検証のみ */ }
}

// メール送信の関心
public class EmailService {
  public void SendWelcomeEmail(string email) { /* メール送信のみ */ }
}

// 通知の関心
public class NotificationService {
  public void NotifyRegistration(string email) { /* 通知のみ */ }
}
```

---

## リファクタリング例②：サービスの組み合わせ ✨

```csharp
public class UserController : Controller
{
  private readonly UserRepository _userRepo;
  private readonly UserValidator _validator;
  private readonly EmailService _emailService;
  private readonly NotificationService _notificationService;

  public IActionResult Register(UserInput input) {
    var validationResult = _validator.Validate(input);
    if (!validationResult.IsValid) {
      ViewBag.Error = validationResult.ErrorMessage;
      return View();
    }

    if (_userRepo.EmailExists(input.Email)) {
      ViewBag.Error = "すでに登録されています";
      return View();
    }

    var user = new User(input.Email, input.Password, input.Name);
    _userRepo.CreateUser(user);
    _emailService.SendWelcomeEmail(input.Email);
    _notificationService.NotifyRegistration(input.Email);

    return RedirectToAction("Index");
  }
}
```

**変更の影響が局所化された！** ✅

---

## 明日からできること 💪

**1. 自分に問いかける習慣**
「この処理、本当にここに書くべき？」
「複数の関心ごとが混ざっていないか？」

**2. AIに問いただす**
「単一責任原則（SRP）を守ってる？」
「関心の分離できてる？」
→ CLEAN・SOLIDの原則名を使って確認

---

## もっと深く学ぶには 📚

### 超推奨 ⭐⭐⭐⭐⭐

**「Architecture to Design より良い設計を目指して」**
米久保剛氏 @ Developers Summit 2025

全75ページ、CLEAN設計原理を詳しく解説
**今日の内容の100倍濃い！**

https://www.docswell.com/s/tyonekubo/5R2Y4E-architecture2design

---

## まとめ 📝

✅ **設計原理「関心の分離」を学んだ**

✅ **AI時代は評価能力が重要**

✅ **明日からコードレビューで意識しよう**

✅ **米久保氏の資料で深く学ぼう**

---

## ちなみに、この資料は... 📊

**[Marp](https://marp.app/)** でMarkdownからHTML生成
- Markdown Presentation Ecosystem
- HTML、PDF、PowerPointに出力可能

**[Claude Code](https://claude.com/claude-code)** でほぼ作成
- AIペアプログラミングツール
- プレゼンテーション構成・コード例・スタイリング

**[Gemini](https://gemini.google.com/)** で挿絵を生成
- AI画像生成ツール

**ご清聴ありがとうございました** 🙏
