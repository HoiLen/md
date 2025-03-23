# asdfでviteのreact-tsプロジェクトの作成

## はじめに

`asdf` で `nodejs` `pnpm` をインストールし、`vite` で `react-ts(React + TypeScript)` プロジェクトを作成する手順を説明する

## 前提

`asdf v0.16.0` 以降をインストール済み

## nodejs のインストール

ホームディレクトリに移動

```bash
cd
```

`.default-npm-packages` ファイルをホームディレクトリに作成し、ファイルを編集

```bash
touch .default-npm-packages

vi .default-npm-packages
```

`.default-npm-packages` に以下の内容を書く

```txt
typescript
ts-node
typesync
npm-check-updates
```

`asdf` で `nodejs` をインストール

```bash
asdf plugin add nodejs // プラグインを追加

asdf install nodejs latest // nodejs の最新バージョンをインストール

asdf list nodejs
23.10.0 // インストールした nodejs のバージョンを出力

asdf set -u nodejs 23.10.0 // グローバルに使う nodejs のバージョンを指定
```

これで `nodejs` の導入完了

```bash
node --version

v23.10.0
```

バージョンが出力されていれば導入成功

## pnpm のインストール

`nodejs` のときと同様に、`asdf` で `pnpm` をインストール

```bash
asdf plugin add pnpm // プラグインに追加

asdf list all pnpm // バージョンをすべて出力する
  .
  .
  .
10.5.2
10.6.0
10.6.1
10.6.2
10.6.3
10.6.4
10.6.5 // ← 最新

asdf install pnpm 10.6.5 // 最新バージョンをインストール

asdf set -u pnpm 10.6.5 // グローバルに使う pnpm のバージョンを指定
```

これで `pnpm` の導入完了

```bash
pnpm --version

10.6.5
```

バージョンが出力されていれば導入成功

## vite で React + TypeScript のプロジェクトを作成する

任意のワークスペースに移動する（なければ `mkdir` で作成する）

```bash
cd ~/dev/web
```

`pnpm` コマンドでプロジェクトを作成する

```bash
pnpm create vite プロジェクト名 --template=react-ts

// 出力
.../aqwsedrftgyhuik |   +1 +
.../aqwsedrftgyhuik | Progress: resolved 1, reused 0, downloaded 1, added 1, done
│
◇  Scaffolding project in /home/username/dev/web/プロジェクト名...
│
└  Done. Now run:

  cd プロジェクト名
  pnpm install
  pnpm run dev
```

出力された最後の3行の指示に従ってコマンドを実行する

```bash
cd プロジェクト名
pnpm install
pnpm run dev
```
