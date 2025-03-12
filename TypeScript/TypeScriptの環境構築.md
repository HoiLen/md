# TypeScriptの環境構築
## Node.js の導入
Node.jsを公式サイトからインストール

インストールが終わったらバージョンの確認

`Git Bash` などのターミナルで以下のコマンドを実行
```bash
node -v

v22.14.0
```
```bash
npm -v

10.9.2
```
バージョン情報が出力されれば OK

## プロジェクトの初期化
### プロジェクトフォルダの作成
`Git Bash` などのターミナルで任意の workspace フォルダに移動
```bash
cd workspaceのパス
```

プロジェクトのフォルダを作成して移動
```bash
mkdir ts-basic
cd ts-basic
```

### npm で環境構築

`npm` コマンドで初期化
```bash
npm init
```

上のコマンドを実行すると `package.json` の初期設定を聞かれる

```
package name: (ts-basic)
version: (1.0.0)
description:
entry point: (index.js)
test command:
git repository:
keywords:
author:
license: (ISC)
About to write to C:\dev\user\web\ts-basic\package.json:

{
  "name": "ts-basic",
  "version": "1.0.0",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC",
  "description": ""
}


Is this OK? (yes)
```

特に指定が無い場合はすべて `Enter` で OK

`ls` コマンドを実行すると `package.json` が生成されたことを確認できる
```bash
ls -l

total 1
-rw-r--r-- 1 user num num month day time package.json
```

`npm install --save-dev` でパッケージのインストール

```bash
npm install --save-dev typescript ts-loader webpack webpack-cli webpack-dev-server
```

[!NOTE] `--save-dev` オプションについて
開発環境でしか使わないパッケージはこのオプションでインストールする

* インストールした各パッケージについて
    * `typescript` : TypeScript 構文を JavaScript 構文に変換するコンパイラ
    * `ts-loader` : webpack と連動して TypeScript コンパイラを起動
    * `webpack` : 複数のファイルを一つにまとめる
    * `webpack-cli` : webpack をコマンドラインで使う
    * `webpack-dev-server` : 
      * webpack のビルド
      * 開発用 Web サーバの起動
      * ホットリロード(ファイルの変更の自動検知と再読み込み)