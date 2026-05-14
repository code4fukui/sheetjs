# [SheetJS](https://sheetjs.com)

SheetJS Community Edition は、ほぼすべての複雑なスプレッドシートから有用なデータを抽出し、レガシーソフトウェアと最新のソフトウェアの両方で動作する新しいスプレッドシートを生成するための、実績のあるオープンソースソリューションを提供します。

[SheetJS Pro](https://sheetjs.com/pro) はデータ処理にとどまらないソリューションを提供します。複雑なテンプレートの簡単な編集、スタイリングによる自由なデザイン、画像・グラフ・ピボットテーブルを用いたカスタムシートの作成、数式の評価と計算ロジックのWebアプリへの移植、一般的なスプレッドシート作業の自動化など、多彩な機能を備えています！

![ライセンス](https://img.shields.io/github/license/SheetJS/sheetjs)

[
![ビルドステータス](https://img.shields.io/github/workflow/status/sheetjs/sheetjs/Tests:%20node.js)
](https://github.com/SheetJS/sheetjs/actions)
[
![Snyk 脆弱性](https://img.shields.io/snyk/vulnerabilities/github/SheetJS/sheetjs)
](https://snyk.io/test/github/SheetJS/sheetjs)
[
![npm ダウンロード数](https://img.shields.io/npm/dm/xlsx.svg)
](https://cdn.sheetjs.com/)
[
![GitHub リポジトリのスター数](https://img.shields.io/github/stars/SheetJS/sheetjs?style=social)
](https://github.com/SheetJS/sheetjs)

## ドキュメント

- **[APIおよび使用方法のドキュメント](https://docs.sheetjs.com)**
- [ダウンロード可能なスクリプトとモジュール](https://cdn.sheetjs.com)
- [ライブデモ](https://oss.sheetjs.com/sheetjs/)

## インストール

お好みのパッケージマネージャーでインストールできます:
```bash
npm install xlsx
# yarn add xlsx
# pnpm add xlsx
```

ブラウザ環境では、以下のスクリプトタグを追加します:
```html
<script src="https://cdn.sheetjs.com/xlsx-latest/package/dist/xlsx.full.min.js"></script>
```

## 使い方

### ファイルの読み込み

この例では、Node.jsでファイルを読み込み、最初のワークシートをオブジェクトのJSON配列に変換します。

```javascript
import { readFile, utils } from 'xlsx';

// ファイルを読み込み
const workbook = readFile("presidents.xlsx");

// 最初のワークシートを取得
const worksheet = workbook.Sheets[workbook.SheetNames[0]];

// ワークシートをJSONに変換
const data = utils.sheet_to_json(worksheet);

console.log(data);
/*
[
  { Name: 'Barack Obama', Index: 44 },
  { Name: 'Donald Trump', Index: 45 }
]
*/
```

### ファイルの書き込み

この例では、オブジェクトのJSON配列から新しいワークブックを作成し、新しいXLSXファイルとして書き出します。

```javascript
import { utils, writeFileXLSX } from 'xlsx';

const data = [
  { Name: "Bill Clinton", Index: 42 },
  { Name: "GeorgeW Bush", Index: 43 }
];

// JSONデータから新しいワークシートを作成
const worksheet = utils.json_to_sheet(data);

// 新しいワークブックを作成しワークシートを追加
const workbook = utils.book_new();
utils.book_append_sheet(workbook, worksheet, "Presidents");

// ワークブックをファイルに書き込み
writeFileXLSX(workbook, "SheetJS.xlsx");
```

## デモと連携

[`demos`](demos/) ディレクトリでは、幅広い連携例や使用パターンを紹介しています。

**フレームワークとAPI**
- [Angular](demos/angular2/)、[AngularJS (1.x)](demos/angular/)
- [React](demos/react/)、[React Native](demos/react/)
- [Vue 2.x](demos/vue/)、[Vue 3.x](demos/vue/modify/)
- [Node.js HTTPサーバー](demos/server/)
- [データベース (SQLite, WebSQL)](demos/database/)

**バンドラーとツール**
- [Webpack](demos/webpack/)
- [Parcel](demos/parcel/)
- [Rollup](demos/rollup/)
- [Browserify](demos/browserify/)
- [TypeScript](demos/typescript/)

**プラットフォームと連携**
- [Deno](demos/deno/)
- [Electron](demos/electron/) および [NW.js](demos/nwjs/)
- [Chrome / Chromium 拡張機能](demos/chrome/)
- [「サーバーレス」関数 (AWS, Azure, Firebase)](demos/function/)
- [ヘッドレスブラウザ (Puppeteer, PhantomJS)](demos/headless/)
- [Internet Explorer (IE6-11)](demos/oldie/)
- [Google Sheets API](https://docs.sheetjs.com/docs/getting-started/demos/gsheet)
- [Adobe ExtendScript](https://docs.sheetjs.com/docs/getting-started/demos/extendscript)

## 同梱パッケージ

本リポジトリは、関連するツールやライブラリを含むモノレポ（monorepo）です。

| パッケージ | 説明 |
| :------ | :---------- |
| [`xlsx`](.) | スプレッドシートファイルの読み書きを行うコアライブラリ。 |
| [`ssf`](packages/ssf) | ECMA-376 数値フォーマットライブラリ。 |
| [`xlsx-cli`](packages/xlsx-cli/) | ファイル処理用の Node.js コマンドラインツール。 |
| [`otorp`](packages/otorp) | Mach-O バイナリから Protocol Buffer v2 の定義を復元するツール。 |
| [`s`](packages/s) | OfficeJS Excel API に準拠したラッパー。 |

## 関連プロジェクト

- <https://oss.sheetjs.com/notes/>: ファイルフォーマットに関するノート
- [`test_files`](https://github.com/SheetJS/test_files): サンプルスプレッドシート
- [`cfb`](https://github.com/SheetJS/js-cfb): コンテナ (OLE/ZIP) フォーマットライブラリ
- [`codepage`](https://github.com/SheetJS/js-codepage): レガシーテキストエンコーディング

## ライセンス

詳細は添付の [LICENSE](LICENSE) ファイルを参照してください。Apache 2.0 License によって明示的に付与されていないすべての権利は、原著作者に帰属します。
