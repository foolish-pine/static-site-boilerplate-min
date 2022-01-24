# 静的サイトボイラープレート（最小構成）
- 静的サイト制作のためのボイラープレートです
- Visual Studio CodeとそのプラグインおよびNode.jsを使用します
- HTML、CSS、JavaScriptの使用を想定しています
- 必要に応じて拡張することができます

## 動作確認環境
Node.js v16.13.1

## 使い方
1. zip形式で本レポジトリをダウンロードする
2. zipファイルを解凍し、フォルダ名を任意のプロジェクト名に変更する
3. プロジェクトのディレクトリに移動し、`npm i`コマンドを実行してパッケージをインストールする
4. [必要なVisual Studio Codeプラグイン](https://github.com/foolish-pine/static-site-boilerplate-min#visual-studio-code%E3%83%97%E3%83%A9%E3%82%B0%E3%82%A4%E3%83%B3)をインストール・有効化する
5. 必要に応じて、README.mdや各種設定ファイルを編集する
6. コーディングを開始する

## 設定ファイルについての説明
### .vscodeディレクトリ
Visual Studio Codeの設定ファイルを格納するディレクトリ。<br>
このディレクトリのファイルに記述した設定はプロジェクト内でのみ有効となる。個人の環境に応じて新規ファイルを追加してよい。<br>
**プロジェクトをGitで管理する場合、.vscodeディレクトリは追跡対象としない。**

### .vscode/extensions.json
プロジェクトにおけるVisual Studio Codeの推奨プラグインを記述したファイル。

### .vscode/settings.json
Visual Studio Codeの設定ファイル。個人の環境に応じて編集可。

### .gitignore
Gitの追跡対象にしないファイル・ディレクトリを記述する。必要に応じて追記可。<br>
プロジェクトをGitで管理する場合、以下のファイル・ディレクトリは追跡対象としない。
- `node_modules`
- `.DS_Store`
- `.vscode`

### .editorconfig
EditorConfigの設定ファイル。使用するルールについては後述。

### .eslintrc.json
ESlintの設定ファイル。使用するルールについては後述。

### .stylelintrc.json
stylelintの設定ファイル。使用するルールについては後述。

### package.json
プロジェクトで使用するパッケージを記載したファイル。

### package-lock.json
使用するパッケージのバージョンを固定するためのファイル。

### README.md
本ドキュメント。プロジェクトに応じて編集可。

## コーディングルール
### コーディング全般
#### 対応ブラウザ
以下のブラウザの最新バージョンを対応ブラウザとする。
- iOS Safari
- Android Google Chrome
- Safari
- Microsoft Edge
- Google Chrome
- Firefox

プロジェクトの要件に合わせて変更すること。

#### [EditorConfig](https://editorconfig.org/)のルール
- `indent_style = tab` … インデントにタブを使用する。この選択は[WordPressのコーディング規約](https://developer.wordpress.org/coding-standards/wordpress-coding-standards/php/#indentation)に依る。プロジェクトの要件に合わせて変更してもよい
- `indent_size = 2` … インデントサイズは2とする。プロジェクトの要件に合わせて変更してもよい
- `end_of_line = lf` … 改行コードはLFとする
- `charset = utf-8` … 文字コードはUTF-8とする
- `trim_trailing_whitespace = true` … 文末のスペースを削除する
- `insert_final_newline = true` … ファイルの最終行に空行を挿入する

#### コメント
必要に応じてコメントを挿入する。<br>
ただし、不要なコメントは削除する。なんらかの理由でコメントアウトしたコードを残す場合は、その理由もコメントで残しておく。

### HTML
#### フォーマッター
- [Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)を使用する

### CSS
#### リンター
- [stylelint](https://stylelint.io/)を使用する
- ベースのルールとして[stylelint-config-standard](https://github.com/stylelint/stylelint-config-standard)を使用する
- 以下のルールを追加する

["declaration-block-no-redundant-longhand-properties": null](https://stylelint.io/user-guide/rules/list/declaration-block-no-redundant-longhand-properties/)<br>
プロパティのロングハンド指定を許容する。
```
// 以下は許容される
a {
  padding-top: 1px;
  padding-right: 2px;
  padding-bottom: 3px;
  padding-left: 4px;
}
```

["keyframes-name-pattern": null](https://stylelint.io/user-guide/rules/list/keyframes-name-pattern/)<br>
keyframeの命名パターンを制限しない。

["selector-class-pattern": null](https://stylelint.io/user-guide/rules/list/selector-class-pattern/)<br>
classセレクタの命名パターンを制限しない。

["selector-id-pattern": null](https://stylelint.io/user-guide/rules/list/selector-id-pattern/)<br>
idセレクタの命名パターンを制限しない。

#### フォーマッター
- [Prettier](https://prettier.io/)を使用する
- ベースのルールとして[stylelint-prettier/recommended](https://github.com/prettier/stylelint-prettier)を使用する
- プロパティの並び順は[stylelint-config-recess-order](https://github.com/stormwarning/stylelint-config-recess-order)を使用する

### JavaScript
#### リンター
- [ESLint](https://eslint.org/)を使用する
- ベースのルールとして[eslint:recommended](https://eslint.org/docs/rules/)を使用する
- 加えて、以下のルールを追加する。ルールの詳細は[こちら](https://eslint.org/docs/rules/)を参照すること。
	- `"no-alert": "warn"` … `alert`, `confirm`, `prompt`が使用されていたら警告する
	- `"no-console": "warn"` … `console`が使用されていたら警告する
	- `"no-unused-vars": "warn"` … 未使用の変数があれば警告する
	- `"no-var": "warn"` … `var`が使用されていたら警告する
	- `"eqeqeq": "warn"` … `==`または`!=`が使用されていたら警告する

#### フォーマッター
- [Prettier](https://prettier.io/)を使用する

### Visual Studio Codeプラグイン
以下のプラグインを使用すること。

- [EditorConfig for VS Code](https://marketplace.visualstudio.com/items?itemName=EditorConfig.EditorConfig)
- [Prettier - Code formatter](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)
- [stylelint](https://marketplace.visualstudio.com/items?itemName=stylelint.vscode-stylelint)
- [ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)
