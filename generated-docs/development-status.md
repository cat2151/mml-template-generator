Last updated: 2025-11-10

# Development Status

## 現在のIssues
- [Issue #4](../issue-notes/4.md) は、複数音源対応MMLにおける音源ごとのテンプレート追加とGUIのプルダウン実装を求めています。
- [Issue #3](../issue-notes/3.md) では、簡易的な楽曲サンプル出力機能の追加を通じて、MML初心者向けに利用の幅を広げることを目指しています。
- [Issue #2](../issue-notes/2.md) と [Issue #1](../issue-notes/1.md) は、オクターブ反転ボタンや音長・音色設定を含むより高度なMMLテンプレートの追加によるMML生成機能の改善を目指しています。

## 次の一手候補
1. [Issue #2](../issue-notes/2.md): オクターブ上下反転ボタンの追加
   - 最初の小さな一歩: `index.html` にオクターブ上下反転ボタンを追加し、クリックイベントを `controller.js` にバインドする。
   - Agent実行プロンプト:
     ```
     対象ファイル: index.html, controller.js

     実行内容: `index.html`に「オクターブ上下反転」ボタンを追加し、`ng-click="toggleOctaveInversion()"`を割り当ててください。また、`controller.js`に`$scope.toggleOctaveInversion`関数をスタブとして追加してください。実装は後続のタスクとして残します。

     確認事項: ボタンがUIに正しく表示され、クリックイベントがAngularJSのスコープにバインドされていることを確認してください。既存のUIレイアウトを崩さないように配置を検討してください。

     期待する出力: `index.html`と`controller.js`の変更内容を示すコードブロック。
     ```

2. [Issue #1](../issue-notes/1.md): もう一段階高度なMMLテンプレートの追加
   - 最初の小さな一歩: ラジオボタンを追加し、最低限のテンプレート追加のON/OFFを切り替えられるようにし、`controller.js`でその状態を管理する変数を追加する。
   - Agent実行プロンプト:
     ```
     対象ファイル: index.html, controller.js

     実行内容: `index.html`に「最低限のテンプレートを追加」というラジオボタン（on/off）を追加し、`ng-model="addBasicTemplate"`として`controller.js`のスコープ変数と紐付けてください。デフォルトは`off`に設定してください。

     確認事項: ラジオボタンがUIに正しく表示され、状態変更が`controller.js`の`$scope.addBasicTemplate`変数に反映されることを確認してください。既存のMML生成ロジックには影響を与えないようにしてください。

     期待する出力: `index.html`と`controller.js`の変更内容を示すコードブロック。
     ```

3. [Issue #4](../issue-notes/4.md): 複数音源対応MMLにおける音源ごとのテンプレート追加とGUIの変更
   - 最初の小さな一歩: `index.html`に音源選択用のプルダウンを追加し、`mckc`が選択されている場合の初期選択肢を設定する。`controller.js`に音源選択用の変数を追加する。
   - Agent実行プロンプト:
     ```
     対象ファイル: index.html, controller.js

     実行内容: `index.html`の「出力MMLフォーマット」のプルダウンの下に、「音源選択」という新しい`<select>`要素と`ng-model="selectedToneSource"`を追加してください。最初の選択肢として、`mckc`が選択されている場合に「2A03(ファミコン音源)」と「RP2C33(ファミコンディスクシステム音源)」を表示するように記述してください。`controller.js`に`$scope.selectedToneSource`と`$scope.toneSources`をスタブとして追加してください。

     確認事項: 新しいプルダウンがUIに正しく表示され、`compiler`の選択に応じて`toneSources`の選択肢が動的に変更される初期ロジックの準備を確認してください。現在のMML生成ロジックに影響を与えないこと。

     期待する出力: `index.html`と`controller.js`の変更内容を示すコードブロック。

---
Generated at: 2025-11-10 08:35:09 JST
