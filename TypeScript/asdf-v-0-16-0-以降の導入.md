# asdf v0.16.0以降の導入方法

## はじめに

パッケージマネージャの `asdf` がv0.16.0から大幅な更新があり、導入方法が少し面倒になった

そこで、`asdf` を Linux に導入する手順を説明する

## 環境

- Windows11
- WSL2
- Ubuntu-24.04
- ターミナル : bash

Linux 環境に `asdf` を入れるため、Windows11 の PC に WSL2 とその中に Ubuntu を入れておく

## 参考

参考にした記事をここに示す

[asdf(v0.16.0)を使ったPython環境構築](https://qiita.com/QiitaTakenoko/items/4100f95803c7dd43e071)

## asdf のインストール

ここから実際の手順を示す

任意の `$PATH` ディレクトリまで移動する

おすすめは以下のパス (デフォルトで `$PATH` となっているため)

```bash
cd /usr/local/bin
```

[asdf のバイナリ (github)](https://github.com/asdf-vm/asdf/releases)

このリンクにある最新バージョンの `asdf-v0.16.x-linux-amd64.tar.gz` をダウンロードする(以下のコマンドで)

```bash
sudo curl -OL https://github.com/asdf-vm/asdf/releases/download/v0.16.x/asdf-v0.16.x-linux-amd64.tar.gz
```

`v0.16.x` の `x` はバージョンによって変更

ダウンロードしたファイルを解凍して削除

```bash
sudo tar -zxvf asdf-v0.16.x-linux-amd64.tar.gz

sudo sudo rm asdf-v0.16.x-linux-amd64.tar.gz
```

もと居たディレクトリに戻る

```bash
cd
```

`shims` ディレクトリを `$PATH` に追加

```bash
echo 'export PATH="${ASDF_DATA_DIR:-$HOME/.asdf}/shims:$PATH"' >> ~/.bashrc
```

`bashrc` をリロード

```bash
source ~/.bashrc
```

これで `asdf` 導入完了となる

```bash
asdf --version //実行

v0.16.x //出力
```

上のように出力されれば `asdf` の導入は成功
