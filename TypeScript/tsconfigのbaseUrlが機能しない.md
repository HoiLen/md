# tsconfig の baseUrl が機能しない
`import` のパスを確認しても `baseUrl` が機能してくれない

## 原因
webpack側でtsconfigのpath設定を読み取るパッケージが無かった
## 解決策
webpack用のパッケージ `tsconfig-paths-webpack-plugin` が必要なのでインストールする
```bash
npm install --save-dev tsconfig-paths-webpack-plugin
```
`webpack.config.js` に以下を追記する
```js
const TsconfigPathsPlugin = require('tsconfig-paths-webpack-plugin')

module.exports = {
    resolve: {
        plugins: [new TsconfigPathsPlugin()],
  },
}
```