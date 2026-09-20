# MarkdownEditor

ブラウザだけで動く、単一HTMLファイルのMarkdownエディタです。左に書くと右にすぐ表示されます。

ビルド不要・インストール不要。`index.html` をブラウザで開けば、それだけで動きます。

## 機能

- **ライブプレビュー** — 左右2ペイン。エディタのスクロールにプレビューが追従します
- **自動保存** — 書いた内容はブラウザの localStorage に残るので、閉じても次回そのまま続きから書けます
- **ファイル操作** — `.md` として保存、既存ファイルを開く、エディタへのドラッグ&ドロップに対応
- **HTML書き出し** — スタイルを埋め込んだ、そのまま公開できる1枚のHTMLを出力します
- **文字数表示** — 空白・改行を除いた文字数と、400字詰め原稿用紙の換算枚数
- **レスポンシブ** — 画面幅が820px以下では「編集／プレビュー」のタブ切り替えになります

## キーボードショートカット

| 操作 | キー |
| --- | --- |
| `.md` として保存 | `Ctrl` / `⌘` + `S` |
| 太字 | `Ctrl` / `⌘` + `B` |
| 斜体 | `Ctrl` / `⌘` + `I` |

## 使い方

リポジトリを clone するか `index.html` をダウンロードして、ブラウザで開くだけです。

```bash
git clone https://github.com/masatakeya/MarkdownEditor.git
```

## Markdownの記法

GitHub Flavored Markdown（表、タスクリスト、取り消し線など）に対応しています。改行はそのまま改行として扱われます。

## 依存ライブラリ

CDN から読み込んでいます。

- [marked](https://marked.js.org/) 12.0.2 — Markdownの変換
- [DOMPurify](https://github.com/cure53/DOMPurify) 3.1.6 — 変換結果のサニタイズ
- Google Fonts — M PLUS 1 Code / Noto Serif JP

そのため、**プレビューにはネットワーク接続が必要です**。読み込めなかった場合はその旨を画面に表示します。

## 安全性について

Markdownの変換結果は必ず DOMPurify を通してから表示しているため、スクリプトを含む文書を開いても実行されません。本文中のリンクには `rel="noopener noreferrer"` を付けた上で別タブで開きます。

## ライセンス

[MIT License](LICENSE)
