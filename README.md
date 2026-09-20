# MarkdownEditor

ブラウザだけで動く、単一HTMLファイルのMarkdownエディタです。左に書くと右にすぐ表示されます。

ビルド不要・インストール不要。`index.html` をブラウザで開けば、それだけで動きます。ライブラリも同梱しているので、**ネットワークに繋がっていなくても動きます**。

**→ [今すぐ使う](https://masatakeya.github.io/MarkdownEditor/)**

## 機能

- **ライブプレビュー** — 左右2ペイン。エディタのスクロールにプレビューが追従します
- **日本語入力に配慮** — 変換中は再描画を止めるので、長い文章でも入力が引っかかりません
- **書くための補助** — 箇条書き・番号付きリスト・引用は改行すると次の行にも続きます。`Tab` で字下げ、太字と斜体はトグル式
- **自動保存** — 書いた内容はブラウザに残るので、閉じても次回そのまま続きから書けます
- **ファイル操作** — `.md` の保存と上書き保存、ファイルを開く、ドラッグ&ドロップに対応
- **画像の貼り付け** — クリップボードの画像をそのまま貼ると、本文に埋め込まれます
- **HTML書き出し** — スタイルを埋め込んだ、そのまま公開できる1枚のHTMLを出力します。見出しが3つ以上あれば目次が付きます
- **ダークモード** — OSの設定に合わせて自動で切り替わります
- **印刷** — `Ctrl / ⌘ + P` でプレビューだけがきれいに印刷されます
- **レスポンシブ** — 画面幅が820px以下では「編集／プレビュー」のタブ切り替えになります

## キーボードショートカット

| 操作 | キー |
| --- | --- |
| 保存（開いているファイルに上書き） | `Ctrl` / `⌘` + `S` |
| 名前を付けて保存 | `Ctrl` / `⌘` + `Shift` + `S` |
| 太字（もう一度押すと解除） | `Ctrl` / `⌘` + `B` |
| 斜体（もう一度押すと解除） | `Ctrl` / `⌘` + `I` |
| 字下げ／戻す | `Tab` / `Shift` + `Tab` |
| 入力欄から抜ける | `Escape` |

`Tab` は字下げに使うためフォーカス移動には使えません。キーボードだけで操作するときは `Escape` で入力欄から抜けてください。

## 使い方

上の公開ページ（https://masatakeya.github.io/MarkdownEditor/ ）を開けば、そのまま使えます。

手元で動かしたい場合は、リポジトリを clone するか `index.html` をダウンロードして、ブラウザで開くだけです。USBメモリに入れて持ち運んでも、機内で開いても動きます。

```bash
git clone https://github.com/masatakeya/MarkdownEditor.git
```

## 保存のしかた

Chrome や Edge では「保存」を押すと保存先を尋ね、次からは同じファイルに上書きします。普通のエディタと同じ感覚で `Ctrl + S` を押せます。

Safari や Firefox のように[この機能](https://developer.mozilla.org/ja/docs/Web/API/File_System_API)がないブラウザでは、従来どおりダウンロードとして保存されます。

なお、書いた内容はブラウザにも自動で残りますが、これは補助です。大事な原稿は `.md` として保存してください。

## Markdownの記法

GitHub Flavored Markdown（表、タスクリスト、取り消し線など）に対応しています。改行はそのまま改行として扱われます。

## 同梱ライブラリ

CDN ではなく `index.html` に直接埋め込んでいます。ネットワークもCDNへの信頼も必要ありません。

| ライブラリ | バージョン | 用途 | ライセンス |
| --- | --- | --- | --- |
| [marked](https://marked.js.org/) | 12.0.2 | Markdownの変換 | MIT |
| [DOMPurify](https://github.com/cure53/DOMPurify) | 3.1.6 | 変換結果のサニタイズ | Apache-2.0 / MPL-2.0 |

いずれも cdnjs 配布の最小化版をそのまま埋め込んでいます（ライセンス表記も残してあります）。取得元と完全性は次の通りです。

```
marked.min.js  sha384-/TQbtLCAerC3jgaim+N78RZSDYV7ryeoBCVqTuzRrFec2akfBkHS7ACQ3PQhvMVi
purify.min.js  sha384-+VfUPEb0PdtChMwmBcBmykRMDd+v6D/oFmB3rZM/puCMDYcIvF968OimRh4KQY9a
```

見た目のフォント（M PLUS 1 Code / Noto Serif JP）だけは Google Fonts から読み込みます。読み込めない場合はOS標準のフォントで表示されるため、オフラインでも支障なく使えます。

## 安全性について

Markdownの変換結果は必ず DOMPurify を通してから表示しているため、スクリプトを含む文書を開いても実行されません。本文中のリンクには `rel="noopener noreferrer"` を付けた上で別タブで開きます。

## ライセンス

[MIT License](LICENSE)
