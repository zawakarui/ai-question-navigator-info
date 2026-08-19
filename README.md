# AI質問ナビゲーター - 情報サイト

Claude、ChatGPT、Gemini、Perplexity、Microsoft Copilotに対応した質問ナビゲーション機能を提供するChrome拡張機能です。長い会話の中から質問を自動検出し、素早くアクセスできるサイドバーを表示します。

![AI質問ナビゲーター](https://img.shields.io/badge/Version-1.4.1-blue) ![License](https://img.shields.io/badge/License-MIT-green) ![Chrome Extension](https://img.shields.io/badge/Chrome-Extension-yellow)

## 🔗 リンク

- **情報サイト**: [https://zawakarui.github.io/ai-question-navigator-info/](https://zawakarui.github.io/ai-question-navigator-info/)
- **Chrome Web Store**: [AI Question Navigator](https://chromewebstore.google.com/detail/iehaefcnohajfglikbpobcjohkfmldjk)

## ✨ 主な機能

### 🎯 統合サポート
- **Claude.ai** - Claude AI チャット
- **ChatGPT** - OpenAI ChatGPT
- **Gemini** - Google Gemini AI
- **Perplexity.ai** - Perplexity AI 検索エンジン
- **Microsoft Copilot** - consumer (copilot.microsoft.com) + M365 Copilot Chat (m365.cloud.microsoft) 🆕

### 🔍 自動質問検出
- ユーザーが投稿した質問のみを自動検出
- AI回答との区別機能
- 重複質問の自動除去

### 🎨 統合UI (Geminiベース)
- サイドバー形式での質問一覧表示
- **クリーンな表示**: どのAIサービスかを識別するラベルを非表示にし、質問文が見やすくなりました。
- ドラッグ&ドロップでの位置変更
- リサイズ機能
- 最小化/展開機能

### 🚀 ナビゲーション機能
- 質問クリックで該当箇所へスムーズスクロール
- 質問のハイライト表示
- リアルタイム質問検出

## 📦 インストール方法

### 1. ファイルの準備

```bash
# プロジェクトディレクトリをダウンロード
git clone [repository-url]
cd ai-question-navigator

# または、ZIPファイルをダウンロードして展開
```

### 2. アイコンファイルの作成

`icons/` ディレクトリに以下のPNGファイルを配置：
- `icon16.png` (16x16px)
- `icon48.png` (48x48px)
- `icon128.png` (128x128px)

💡 `icons/icon-template.svg` を [SVG to PNG変換ツール](https://cloudconvert.com/svg-to-png) で変換できます。

### 3. Chrome拡張機能のインストール

1. Chromeで `chrome://extensions/` を開く
2. 右上の「デベロッパーモード」をONにする
3. 「パッケージ化されていない拡張機能を読み込む」をクリック
4. `ai-question-navigator` フォルダを選択
5. 「フォルダーの選択」をクリック

### 4. 動作確認

1. [Claude.ai](https://claude.ai/)、[ChatGPT](https://chatgpt.com/)、[Gemini](https://gemini.google.com/)、[Perplexity.ai](https://www.perplexity.ai/)、[Microsoft Copilot](https://copilot.microsoft.com/) または [M365 Copilot Chat](https://m365.cloud.microsoft/chat) にアクセス
2. 質問を投稿
3. 画面右上にサイドバーが表示されることを確認

## 🎮 使用方法

### 基本操作

| 操作 | 説明 |
|------|------|
| **質問項目クリック** | 該当質問にスムーズスクロール |
| **個別コピーボタンクリック** | 質問テキストのみをコピー |
| **個別コピーボタンShift+クリック** | 質問 + 回答を Markdown 形式でコピー 🆕 |
| **全件コピー（`⎘`）クリック** | 全質問テキストをコピー |
| **全件コピー（`⎘`）Shift+クリック** | 全質問 + 全回答を Markdown 形式でコピー 🆕 |
| **ヘッダードラッグ** | サイドバー位置を移動 |
| **右下角ドラッグ** | サイドバーサイズ変更 |
| **`−`ボタン** | 最小化/展開 |
| **`↻`ボタン** | 質問リスト更新 |
| **`×`ボタン** | サイドバーを閉じる |

### Q+A コピー機能 (v1.3.0)

質問とAI回答をセットで他ツールに転記したいときに使えます。

- **通常クリック**: 質問テキストのみがクリップボードに入ります（v1.2.x 以前と同じ挙動）
- **Shift+クリック**: 質問と回答が Markdown 形式（`## 質問 N` / `## 回答`）でクリップボードに入ります
- **回答が取得できない場合**（仮想スクロールで回答が画面外に unmount されているとき、Gemini の空回答既知バグ等）はフォールバックとして質問のみコピーされ、ボタンの tooltip に「回答未取得、質問のみコピーしました」と表示されます

ボタンにマウスを重ねるとネイティブ tooltip で挙動の説明が表示されるため、Shift キーの存在を覚えていなくても気づける設計になっています。

### デバッグ機能

ブラウザのコンソールで以下のコマンドが使用できます：

```javascript
// 手動更新
aiNavigatorDebug.refresh();

// 質問数確認
aiNavigatorDebug.getQuestionCount();

// サイドバー表示切替
aiNavigatorDebug.toggleSidebar();

// 完全再初期化
aiNavigatorDebug.reinitialize();

// 現在のサービス確認
aiNavigatorDebug.getCurrentService();
```

## 🏗️ 技術仕様

### アーキテクチャ

```
┌──────────────────────────────────────────────────────┐
│              Chrome Extension                        │
├──────────────────────────────────────────────────────┤
│       Unified Question Navigator                     │
├──────────────────────────────────────────────────────┤
│ ┌─────┐ ┌─────┐ ┌─────┐ ┌────────┐ ┌────────┐       │
│ │Claud│ │ChatG│ │Gemin│ │Perplex.│ │ Copilot│       │
│ │ Det.│ │ Det.│ │ Det.│ │ Det.   │ │ Det. 🆕│       │
│ └─────┘ └─────┘ └─────┘ └────────┘ └────────┘       │
├──────────────────────────────────────────────────────┤
│           Navigator UI (共通)                        │
└──────────────────────────────────────────────────────┘
```

### 主要技術

- **Manifest V3** - Chrome Extension API
- **Vanilla JavaScript** - フレームワーク非依存
- **CSS3** - レスポンシブデザイン
- **MutationObserver** - DOM変更監視
- **プラグイン式設計** - サービス別モジュール

## 🔧 開発・保守

### 最近の変更
- サイドバー内だけでCSS変数が適用されるようにスコープを限定し、ダークモード/高コントラストの上書きもサイドバー内に適用。

### ファイル構成

```
ai-question-navigator/
├── manifest.json              # 拡張機能設定
├── content.js                 # メインコントローラー
├── popup.html                 # ポップアップUI
├── popup.js                   # ポップアップ制御
├── modules/                   # 検出器モジュール
│   ├── base-detector.js       # 基底クラス
│   ├── claude-detector.js     # Claude専用
│   ├── chatgpt-detector.js    # ChatGPT専用
│   ├── gemini-detector.js     # Gemini専用
│   ├── perplexity-detector.js # Perplexity専用
│   └── copilot-detector.js    # Microsoft Copilot専用 🆕
├── ui/                        # UI関連
│   ├── navigator-ui.js        # 共通UI
│   └── styles.css            # スタイルシート
├── icons/                     # アイコン類
└── README.md                  # このファイル
```

### カスタマイズ

#### セレクターの追加
新しいDOM構造に対応する場合：

```javascript
// 例：Claude用セレクターの追加
// modules/claude-detector.js
this.selectors = {
  primary: '[data-is-streaming="false"][data-message-author-role="human"]',
  fallback: [
    '.font-user-message',
    '.new-selector-class',  // ← 追加
    // ...
  ]
};
```

#### スタイルのカスタマイズ
テーマ色の変更：

```css
/* ui/styles.css */
:root {
  --claude-color: #ff6b35;      /* Claude橙 */
  --chatgpt-color: #10a37f;     /* ChatGPT緑 */
  --gemini-color: #4285f4;      /* Gemini青 */
  --perplexity-color: #20b2aa;  /* Perplexity水色 */
  --copilot-color: #8B5CF6;     /* Copilot紫 */ 🆕
}
```

### 更新方法

1. ファイルを修正
2. `chrome://extensions/` でリロードボタンをクリック
3. 対象ページをリフレッシュ

## 🐛 トラブルシューティング

### よくある問題

#### Q: サイドバーが表示されない
**A**: 以下を確認してください：
- 対応サイト（Claude.ai、ChatGPT、Gemini、Perplexity.ai、Microsoft Copilot、M365 Copilot Chat）にアクセスしているか
- 拡張機能が有効になっているか
- コンソールエラーがないか

#### Q: 質問が検出されない
**A**: 以下を試してください：
```javascript
// コンソールで実行
aiNavigatorDebug.refresh();
aiNavigatorDebug.getQuestionCount();
```

#### Q: 動作が重い
**A**: 以下で状態を確認：
```javascript
// メモリ使用量確認
console.log(performance.memory);
// 再初期化
aiNavigatorDebug.reinitialize();
```

### エラー対応

| エラーメッセージ | 原因 | 対処法 |
|------------------|------|--------|
| `Selector failed` | DOM構造変更 | セレクター更新 |
| `No questions found` | 検出失敗 | 手動更新実行 |
| `Script injection failed` | 権限不足 | 拡張機能再インストール |

## 🤝 コントリビューション

### 改善提案・バグレポート

1. **Issue作成** - 具体的な問題を記述
2. **再現手順** - 問題の発生条件を明記
3. **環境情報** - ブラウザ版本・OS等

### 機能追加

1. **Fork** - プロジェクトをフォーク
2. **Branch作成** - 機能ブランチを作成
3. **実装** - コードを追加・修正
4. **Test** - 動作確認
5. **Pull Request** - 変更を提案

## 📝 更新履歴

### v1.4.1 (2026-08-19) 🆕
- 🐛 **Claude Web の UI 刷新で質問が検出されなくなる問題を修正**
- ✅ Claude 側の DOM 構造変更（デザインシステム刷新・仮想スクロール導入）に検出セレクタを追随
- ✅ 会話外の UI 要素（アカウント名）が質問として誤表示される問題を解消
- ✅ 複数段落・長文の質問も全文が正しく抽出されるよう改善
- ✅ Q+A コピー機能の回答抽出を新 DOM 構造に対応
- 🛡️ **設計方針**: 広すぎるワイルドカードセレクタを全廃し、構造ベースの除外判定を第一防御に変更。Claude 専用の回帰テストを新規追加（16 ケース）

### v1.4.0 (2026-05-24)
- 🎉 **Microsoft Copilot 対応を追加**
- ✅ consumer Copilot (`https://copilot.microsoft.com/*`) と M365 Copilot Chat (`https://m365.cloud.microsoft/chat*`) の 2 系統に対応
- ✅ CopilotDetector クラスを新規実装 (consumer/m365 二系統対応、660 行)
- ✅ M365 の仮想スクロール (`fui-Virtualizer`) に対応した累積検出方式
- ✅ Copilot 専用テーマカラー追加 (紫 #8B5CF6)
- ✅ consumer の `data-content="user-message"` ⇔ `data-content="ai-message"` 対称構造を活用
- 🛡️ **設計方針**: content-based fallback (`findUserQueriesByContent`) は不採用 (mavatar 同型バグ予防)。excludePatterns は全て両端 anchor (v1.3.6/v1.3.7 教訓)
- 🐛 v1.4.0 RC 修正: `[data-message-type="Progress"]` が persistent 属性と判明したため、ストリーミング保留分岐を撤廃 (回帰防止テスト追加)

### v1.3.7 (2026-05-22)
- 🔧 **挨拶 excludePattern を両端 anchor 化**
- ✅ 「ありがとうございます。ところで、X?」のような相槌から入る正当な後続質問が検出されるよう base-detector の `isValidQuestion` パターンを修正
- ✅ 純粋な相槌 (「ありがとう」「了解」等) は引き続き除外される回帰非影響を担保

### v1.3.1 (2026-05-11)
- ✨ **「最小化状態でスタート」オプションの追加**
- ✅ popup に ON/OFF トグルを設置し、`chrome.storage.local` で永続化
- ✅ ON の場合は毎回サイドバーを最小化状態（幅 150px、ヘッダーのみ）で起動
- ✅ OFF の場合は従来通り展開状態で起動（デフォルト）
- 🧹 popup ヘッダーから古いバージョン表記（v1.2.2）を削除し、表記乖離を恒久的に解消
- 🛡️ **設計方針**: 既存の `toggleMinimize()` ロジックには手を入れず、初期フラグの起点のみ差し替え（インラインスタイル制御を維持し hover 退行を予防）

### v1.3.0 (2026-05-11)
- ✨ **Q+A コピー機能の追加**
- ✅ 個別コピーボタン Shift+クリックで質問+回答を Markdown 形式でクリップボードへ
- ✅ 全件コピーボタン Shift+クリックで全 Q+A を `---` 区切りで連結してクリップボードへ
- ✅ 通常クリックの挙動（質問のみコピー）は v1.2.x 以前と互換
- ✅ 回答が取得できないとき（仮想スクロール unmount / 空回答）は質問のみコピー + 警告 tooltip にフォールバック
- ✅ ボタンの native tooltip で Shift+クリック挙動を案内
- 🛡️ **設計方針**: 1 ボタン構造を維持し、CSS / hover ロジックを一切変更しないことで過去の hover 退行（v1.1.x 系で発生した copy ボタン消失・位置ズレ）の再発を防止

### v1.2.3 (2026-02-17)
- 🎯 **ChatGPT Codexページのサイドバー位置調整**
- ✅ Codexページ固有メニューとの重なりを回避するため初期位置を下方に調整
- ✅ 通常のChatGPTページや他サービスには影響なし

### v1.2.2 (2026-01-18)
- 🎨 **CSS変数のスコープ調整**
- ✅ サイドバー内だけでCSS変数が有効になるよう適用範囲を限定
- ✅ ダークモード/高コントラストの上書きもサイドバー内に限定

### v1.2.1 (2026-01-11)
- 🔧 **Perplexityの質問検出を改善**
- ✅ 2件目以降の質問も検出するようセレクタを拡張
- ✅ AI回答領域の誤検出を抑制
- 🎯 **サイドバーの初期位置調整**
- ✅ サイドバーの初期表示位置を画面上から50pxに変更

### v1.2.0 (2025-11-11)
- ✨ **コピー機能の追加**
- ✅ すべての質問を一括コピーする機能
- ✅ 個別の質問をコピーする機能（ホバー時に表示）
- ✅ コピー成功時のビジュアルフィードバック
- 🎨 **UIの刷新**
- ✅ Material Icons/Unicode記号を採用し、絵文字から移行
- ✅ サービスアイコン（絵文字）を削除してクリーンなデザインに
- ✅ アイコンサイズと色を最適化

### v1.1.3 (2025-11-08)
- 🔧 **Perplexityの質問検出を改善**
- ✅ 2件目以降の質問も検出するようセレクタを拡張
- ✅ AI回答領域の誤検出を抑制
- 🎯 **サイドバーの初期位置調整**
- ✅ サイドバーの初期表示位置を画面上から50pxに変更

### v1.1.2 (2025-11-07)
- 🔧 **Perplexity URL対応の改善**
- ✅ Perplexityのサイドバー表示を `/search/` パスのみに限定
- ✅ `/spaces`, `/finance`, `/discover` などのページでは非表示に

### v1.1.1 (2025-11-06)
- 🐛 **ダークモード対応の改善** (Issue #4)
- ✅ ChatGPTダークモード時のサイドバー内テキストの視認性を修正
- ✅ システムダークモード時のホバー・クリック状態のコントラストを改善
- ✅ ページ上のハイライト効果を枠線のみに簡素化
- ✅ JavaScriptホバー効果をCSSに統一

### v1.1.0 (2025-10-30)
- 🎉 **Perplexity.ai対応を追加**
- ✅ PerplexityDetectorクラスの実装
- ✅ Lexicalエディタ（`data-lexical-text="true"`）対応
- ✅ 左サイドバー除外ロジック
- ✅ Perplexity専用テーマカラー追加

### v1.0.1 (2025-10-28)
- UI改善: 質問一覧からサービス識別ラベル（`gemini`, `chatgpt`など）を削除し、視認性を向上。

### v1.0.0 (2025-06-18)
- 🎉 初回リリース
- ✅ Claude.ai対応
- ✅ ChatGPT対応
- ✅ Gemini対応
- ✅ 統合UI実装
- ✅ ドラッグ&リサイズ機能
- ✅ デバッグ機能

## 📄 ライセンス

MIT License

## 🙏 謝辞

- **Claude, ChatGPT, Gemini, Perplexity, Microsoft Copilot** - 素晴らしいAIサービスの提供
- **Chrome Extensions API** - 豊富な機能の提供
- **オープンソースコミュニティ** - 参考にさせていただいた多くのプロジェクト

---

**🔗 関連リンク**
- [Chrome Extensions Documentation](https://developer.chrome.com/docs/extensions/)
- [Claude.ai](https://claude.ai/)
- [ChatGPT](https://chatgpt.com/)
- [Gemini](https://gemini.google.com/)
- [Perplexity.ai](https://www.perplexity.ai/)
- [Microsoft Copilot](https://copilot.microsoft.com/) / [M365 Copilot Chat](https://m365.cloud.microsoft/chat)

**📞 サポート**
問題が発生した場合は、[Chrome Web Store のレビュー欄](https://chromewebstore.google.com/detail/iehaefcnohajfglikbpobcjohkfmldjk)からお知らせください。

---

© 2025 AI Question Navigator Development Team
