# npm プロジェクトの共有について

npm で立ち上げる TypeScript のプロジェクトを例にする

`npm init` で npm を初期化し、

```bash
npm install --save-dev typescript ts-loader webpack webpack-cli webpack-dev-server
```

で TypeScript の開発環境に必要なパッケージをインストールする

`--save` オプションにより、パッケージのインストール時に `package.json` の dependencies に依存関係が定義される

```json
{
  "name": "ts-basic",
  "version": "1.0.0",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC",
  "description": "",
  "devDependencies": {
    "ts-loader": "^9.5.2",
    "typescript": "^5.8.2",
    "webpack": "^5.98.0",
    "webpack-cli": "^6.0.1",
    "webpack-dev-server": "^5.2.0"
  }
}
```

この状態で GitHub に Push したとする

次に、別の PC でこのリポジトリを取ってきて開発を進めるとする

まずはクローン

```bash
USER@PC MINGW64 /c/workspace/generalProjects/
git clone GitHubのリポジトリのURL
```

これを実行すると、自動的にカレントディレクトリにリポジトリ名のフォルダが作成され、その中にリポジトリの内容が追加される。

しかし、パッケージ類をインストールしないと、このままでは開発できない

そこで

```bash
npm install
```

これで、クローンをして取得した `package.json` の依存関係を読み込んで、必要なパッケージを自動でインストールしてくれる
