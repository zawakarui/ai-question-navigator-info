# AI質問ナビゲーター - 情報サイト

![AI質問ナビゲーター](https://img.shields.io/badge/Version-1.2.3-blue) ![License](https://img.shields.io/badge/License-MIT-green) ![Chrome Extension](https://img.shields.io/badge/Chrome-Extension-yellow)

AI質問ナビゲーター Chrome拡張機能の公式情報サイトです。プライバシーポリシー、サポート、ドキュメントを提供しています。

## 🔗 リンク

- **情報サイト**: [https://zawakarui.github.io/ai-question-navigator-info/](https://zawakarui.github.io/ai-question-navigator-info/)
- **拡張機能リポジトリ**: [https://github.com/zawakarui/ai-question-navigator](https://github.com/zawakarui/ai-question-navigator)
- **Chrome Web Store**: [AI Question Navigator](https://chromewebstore.google.com/detail/ai-question-navigator)

## 📝 更新履歴

### v1.2.3 (2026-02-17) 🆕
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

MIT License - 詳細は [LICENSE](https://github.com/zawakarui/ai-question-navigator/blob/main/LICENSE) ファイルを参照

## 🙏 謝辞

- **Claude, ChatGPT, Gemini, Perplexity** - 素晴らしいAIサービスの提供
- **Chrome Extensions API** - 豊富な機能の提供
- **オープンソースコミュニティ** - 参考にさせていただいた多くのプロジェクト

---

**🔗 関連リンク**
- [Chrome Extensions Documentation](https://developer.chrome.com/docs/extensions/)
- [Claude.ai](https://claude.ai/)
- [ChatGPT](https://chatgpt.com/)
- [Gemini](https://gemini.google.com/)
- [Perplexity.ai](https://www.perplexity.ai/)

**📞 サポート**
問題が発生した場合は、ブラウザのコンソールログと共に[Issue](https://github.com/zawakarui/ai-question-navigator/issues)を作成してください。

---

© 2025 AI Question Navigator Development Team
