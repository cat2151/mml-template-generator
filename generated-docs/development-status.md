Last updated: 2025-11-11

# Development Status

## 現在のIssues
- MMLテンプレート生成ツールにおいて、現在、複数音源（[Issue #4](../issue-notes/4.md)）やより高度な設定（[Issue #1](../issue-notes/1.md)）に対応するテンプレートの追加が検討されています。
- ユーザー体験向上のため、簡易的な楽曲サンプル出力機能（[Issue #3](../issue-notes/3.md)）と、入力MMLのオクターブ上下反転ボタン（[Issue #2](../issue-notes/2.md)）の実装が求められています。
- これらの機能は、主にMMLテンプレートの利便性向上と、MMLを初めて触るユーザーの学習障壁を低減することを目的としています。

## 次の一手候補
1. [Issue #4](../issue-notes/4.md): テンプレ追加、複数音源利用可能MMLは音源ごとのテンプレも追加する
   - 最初の小さな一歩: `index.html` に音源選択用の新しいプルダウンを追加し、既存のコンパイラ選択（例: `mckc`）に応じてこのプルダウンが表示/非表示されるように `controller.js` でロジックを実装する。
   - Agent実行プロンプ:
     ```
     対象ファイル: `index.html`, `controller.js`

     実行内容: `index.html` に新しい `<select>` 要素として音源選択プルダウンを追加してください。このプルダウンは `ng-model="soundChip"` を持ち、初期選択肢として「ファミコン音源 (2A03)」と「ファミコンディスクシステム音源 (RP2C33)」を含めてください。
     `controller.js` に、`compiler` が `mckc` の場合にのみこの `soundChip` プルダウンが表示されるように `ng-show` の条件を制御するロジックを実装してください。具体的には、`$scope.showSoundChipSelect` のような変数を導入し、`$scope.compiler` の変更時にその値を更新してください。

     確認事項: 既存の `compiler` 選択ロジックや `generate()` 関数への影響がないことを確認してください。新しいプルダウンが既存のUIレイアウトを大きく崩さないように、CSSの調整は不要ですが配置を考慮してください。

     期待する出力: `index.html` および `controller.js` の変更案をMarkdown形式のコードブロックで出力してください。
     ```

2. [Issue #3](../issue-notes/3.md): 楽曲サンプル出力機能をつける
   - 最初の小さな一歩: `index.html` に「楽曲サンプル」セクションを追加し、その中に「シンプルなメロディ（3ch）」という選択肢を持つラジオボタンと、選択されたMMLを表示する読み取り専用のテキストエリアを暫定的に配置する。機能はダミーで良い。
   - Agent実行プロンプト:
     ```
     対象ファイル: `index.html`

     実行内容: `index.html` の既存のMML入力/出力エリアの下に、新しい `div` 要素で「楽曲サンプル」セクションを作成してください。
     このセクション内に、「シンプルなメロディ（3ch）」というラベルを持つラジオボタン（`ng-model="selectedSample"`）と、その選択に応じてMMLが表示される読み取り専用の `textarea` （`ng-model="sampleMMLText"`）を配置してください。
     現時点では、ラジオボタンが選択されても `sampleMMLText` には `cde; cde; cde;` といった固定のダミーMMLが表示されるように、簡単な `ng-change` または初期値を設定してください。

     確認事項: 新しいセクションが既存のMMLテンプレート生成機能のUIと混同されないよう、明確に区切られた配置になっていることを確認してください。既存のAngularJSアプリケーションの構造を壊さないように注意してください。

     期待する出力: `index.html` の変更案をMarkdown形式のコードブロックで出力してください。
     ```

3. [Issue #2](../issue-notes/2.md): オクターブ上下反転ボタンをつける
   - 最初の小さな一歩: `index.html` のページ下部に「オクターブ上下反転」ボタンを配置し、`controller.js` にこのボタンがクリックされたときにコンソールにログを出力するダミー関数を実装する。
   - Agent実行プロンプト:
     ```
     対象ファイル: `index.html`, `controller.js`

     実行内容: `index.html` の出力MMLテキストエリアの下、またはページ下部の適切な位置に、「オクターブ上下反転」というテキストのボタンを追加してください。このボタンには `ng-click="toggleOctaveInversion()"` を設定してください。
     `controller.js` 内に、`$scope.toggleOctaveInversion` 関数を実装してください。この関数は、現時点では `console.log("Octave inversion toggled");` と出力するだけのダミーとし、ロジックの実装は不要です。

     確認事項: ボタンが既存のUIの邪魔にならず、視認性の良い適切な位置にあることを確認してください。既存のAngularJSスコープ内で関数が呼び出されることを確認してください。

     期待する出力: `index.html` および `controller.js` の変更案をMarkdown形式のコードブロックで出力してください。

---
Generated at: 2025-11-11 07:06:35 JST
