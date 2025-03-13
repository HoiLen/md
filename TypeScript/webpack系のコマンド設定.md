# package.json に webpack のコマンドを設定

`"scripts"` の要素に `"build"` `"start"` を追加する

```json
"scripts": {
    "build": "webpack --mode=production",
    "start": "webpack-cli serve --mode development"
}
```
こうすることで、ターミナルで `"build"` や `"start"` コマンドを実行するだけでビルドやサーバーの立ち上げをすることができる