# ESLint と Prettier の設定

## ソースコードの品質を高めるツール

- ESLint
  - JavaScript のための静的検証ツール
  - ファイル内のバグチェックやコーディングスタイルの一貫性を保つ
- Prettier
  - コードフォーマッター
  - ルールに則ってソースコードを整形
  - プロジェクトごとにルールを設定できる

## 設定ファイルの追加

プロジェクトのルートディレクトリに `.prettierrc` と `eslint.config.mjs` を作成

### .prettierrc

```json
{
  "printWidth": 120,
  "singleQuote": true,
  "semi": false
}
```

### .eslint.config.mjs

```js
import typescriptEslint from '@typescript-eslint/eslint-plugin';
import globals from 'globals';
import tsParser from '@typescript-eslint/parser';
import path from 'node:path';
import { fileURLToPath } from 'node:url';
import js from '@eslint/js';
import { FlatCompat } from '@eslint/eslintrc';

const __filename = fileURLToPath(import.meta.url);
const __dirname = path.dirname(__filename);
const compat = new FlatCompat({
  baseDirectory: __dirname,
  recommendedConfig: js.configs.recommended,
  allConfig: js.configs.all,
});

export default [
  ...compat.extends(
    'eslint:recommended',
    'plugin:@typescript-eslint/recommended',
    'prettier'
  ),
  {
    plugins: {
      '@typescript-eslint': typescriptEslint,
    },

    languageOptions: {
      globals: {
        ...globals.browser,
      },

      parser: tsParser,
      ecmaVersion: 5,
      sourceType: 'module',

      parserOptions: {
        project: './tsconfig.json',
      },
    },

    rules: {},
  },
];
```

## package.json を変更

`lint-fix` という名前でコマンドを登録する

```json
// scripts の中に追記
"lint-fix": "eslint --fix \"./src/**/*.{js,ts}\""
```

windows と mac ではパスの書き方が異なるので注意が必要
