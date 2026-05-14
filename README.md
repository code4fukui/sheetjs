# [SheetJS](https://sheetjs.com)

> 日本語のREADMEはこちらです: [README.ja.md](README.ja.md)

The SheetJS Community Edition offers battle-tested open-source solutions for extracting useful data from almost any complex spreadsheet and generating new spreadsheets that will work with legacy and modern software alike.

[SheetJS Pro](https://sheetjs.com/pro) offers solutions beyond data processing: Edit complex templates with ease; let out your inner Picasso with styling; make custom sheets with images/graphs/PivotTables; evaluate formula expressions and port calculations to web apps; automate common spreadsheet tasks, and much more!


![License](https://img.shields.io/github/license/SheetJS/sheetjs)

[
![Build Status](https://img.shields.io/github/workflow/status/sheetjs/sheetjs/Tests:%20node.js)
](https://github.com/SheetJS/sheetjs/actions)
[
![Snyk Vulnerabilities](https://img.shields.io/snyk/vulnerabilities/github/SheetJS/sheetjs)
](https://snyk.io/test/github/SheetJS/sheetjs)
[
![npm Downloads](https://img.shields.io/npm/dm/xlsx.svg)
](https://cdn.sheetjs.com/)
[
![GitHub Repo stars](https://img.shields.io/github/stars/SheetJS/sheetjs?style=social)
](https://github.com/SheetJS/sheetjs)

## Documentation

- **[API and Usage Documentation](https://docs.sheetjs.com)**
- [Downloadable Scripts and Modules](https://cdn.sheetjs.com)
- [Live Demo](https://oss.sheetjs.com/sheetjs/)

## Installation

Install with your favorite package manager:
```bash
npm install xlsx
# yarn add xlsx
# pnpm add xlsx
```

In the browser, add the following script tag:
```html
<script src="https://cdn.sheetjs.com/xlsx-latest/package/dist/xlsx.full.min.js"></script>
```

## Usage

### Reading Files

This example reads a file in Node.js and converts the first worksheet to a JSON array of objects.

```javascript
import { readFile, utils } from 'xlsx';

// Read the file
const workbook = readFile("presidents.xlsx");

// Get the first worksheet
const worksheet = workbook.Sheets[workbook.SheetNames[0]];

// Convert the worksheet to JSON
const data = utils.sheet_to_json(worksheet);

console.log(data);
/*
[
  { Name: 'Barack Obama', Index: 44 },
  { Name: 'Donald Trump', Index: 45 }
]
*/
```

### Writing Files

This example creates a new workbook from a JSON array of objects and writes it to a new XLSX file.

```javascript
import { utils, writeFileXLSX } from 'xlsx';

const data = [
  { Name: "Bill Clinton", Index: 42 },
  { Name: "GeorgeW Bush", Index: 43 }
];

// Create a new worksheet from the JSON data
const worksheet = utils.json_to_sheet(data);

// Create a new workbook and add the worksheet
const workbook = utils.book_new();
utils.book_append_sheet(workbook, worksheet, "Presidents");

// Write the workbook to a file
writeFileXLSX(workbook, "SheetJS.xlsx");
```

## Demos and Integrations

The [`demos`](demos/) directory showcases a wide range of integrations and usage patterns.

**Frameworks and APIs**
- [Angular](demos/angular2/), [AngularJS (1.x)](demos/angular/)
- [React](demos/react/), [React Native](demos/react/)
- [Vue 2.x](demos/vue/), [Vue 3.x](demos/vue/modify/)
- [Node.js HTTP Server](demos/server/)
- [Databases (SQLite, WebSQL)](demos/database/)

**Bundlers and Tooling**
- [Webpack](demos/webpack/)
- [Parcel](demos/parcel/)
- [Rollup](demos/rollup/)
- [Browserify](demos/browserify/)
- [TypeScript](demos/typescript/)

**Platforms and Integrations**
- [Deno](demos/deno/)
- [Electron](demos/electron/) and [NW.js](demos/nwjs/)
- [Chrome / Chromium Extensions](demos/chrome/)
- ["Serverless" Functions (AWS, Azure, Firebase)](demos/function/)
- [Headless Browsers (Puppeteer, PhantomJS)](demos/headless/)
- [Internet Explorer (IE6-11)](demos/oldie/)
- [Google Sheets API](https://docs.sheetjs.com/docs/getting-started/demos/gsheet)
- [Adobe ExtendScript](https://docs.sheetjs.com/docs/getting-started/demos/extendscript)

## Included Packages

This is a monorepo containing related tools and libraries.

| Package | Description |
| :------ | :---------- |
| [`xlsx`](.) | The core library for reading and writing spreadsheet files. |
| [`ssf`](packages/ssf) | ECMA-376 number format library. |
| [`xlsx-cli`](packages/xlsx-cli/) | NodeJS command-line tool for processing files. |
| [`otorp`](packages/otorp) | Recovers Protocol Buffer v2 definitions from Mach-O binaries. |
| [`s`](packages/s) | Wrapper aligned with the OfficeJS Excel API. |

## Related Projects

- <https://oss.sheetjs.com/notes/>: File Format Notes
- [`test_files`](https://github.com/SheetJS/test_files): Sample spreadsheets
- [`cfb`](https://github.com/SheetJS/js-cfb): Container (OLE/ZIP) format library
- [`codepage`](https://github.com/SheetJS/js-codepage): Legacy text encodings

## License

Please consult the attached [LICENSE](LICENSE) file for details. All rights not explicitly granted by the Apache 2.0 License are reserved by the Original Author.