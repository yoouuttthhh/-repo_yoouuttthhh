# プロジェクト名
このリポジトリは開発勉強用のメモです。

## 内容
- URLやコマンド、考察を記録
- Markdownで整理


### タイムライン
2025-10-19 AM11:32
git --version
gitをインストールした

## コマンド例
```bash
npm install
npm start


# Markdown → HTML 変換サンプル（Node.js + marked）

このサンプルは Node.js と `marked` を使って、Markdown ファイルを HTML に変換する方法の解説です。

---

## 1️⃣ モジュールの読み込み

```js
import fs from "fs";
import { marked, Marked } from "marked";

fs → Node.js 標準のファイルシステムモジュール
ファイルの読み書きをするために使う

marked → Markdown を HTML に変換するライブラリ
marked.parse() で Markdown文字列を HTML に変換できる

Marked はこのコードでは使われていませんが、marked のクラスや型情報としてインポート可能

##　2️⃣ Markdownパーサーの設定
marked.use({
    mangle: false,
    headerIds: false
});


marked.use() でオプションを設定

mangle: false → HTML に変換するときにメールアドレスなどを自動で難読化しない

headerIds: false → Markdown の # 見出し に自動で id 属性を付与しない

※ 普通にブログやドキュメントに変換するときに便利なオプションです

##　3️⃣ Markdownファイルの読み込み
const markdownString = fs.readFileSync("sample.md", "utf8");


fs.readFileSync() → 同期的にファイルを読み込む

"sample.md" → 読み込む Markdown ファイルのパス

"utf8" → 文字コードを UTF-8 に指定

これで markdownString に Markdown の文字列が入ります

##　4️⃣ Markdown を HTML に変換
const htmlString = marked.parse(markdownString);


marked.parse() に Markdown 文字列を渡すと、HTML 文字列に変換して返す

例えば # 見出し → <h1>見出し</h1> に変換されます

##　5️⃣ HTML ファイルとして書き出す
fs.writeFileSync("sample.html", htmlString, "utf8");


fs.writeFileSync() → 同期的にファイルを書き込む

"sample.html" → 出力ファイル名

htmlString → 書き込む内容（変換後の HTML）

"utf8" → 文字コード

##　✅ 実行すると

sample.md を読み込む

marked で HTML に変換

sample.html として保存される

つまり Markdown → HTML の変換処理の自動化 です。