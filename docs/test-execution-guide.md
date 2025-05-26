# テスト実行手順書

このドキュメントでは、計算練習アプリのテスト実行方法について詳細に説明します。

## 前提条件

- Node.js（バージョン22.14.0以上）がインストールされていること
- pnpm（バージョン8.0.0以上）がインストールされていること
- リポジトリがクローンされていること

## 環境セットアップ

```bash
# 依存パッケージのインストール
pnpm install
```

## テストコマンド

### 基本的なテスト実行

```bash
# すべてのテストを実行
pnpm test

# 監視モードでテストを実行（ファイル変更を検知して自動実行）
pnpm test:watch

# テストカバレッジレポートを生成
pnpm test:coverage
```

テストカバレッジレポートは `coverage/` ディレクトリに生成されます。
`coverage/lcov-report/index.html` をブラウザで開くと、詳細なカバレッジレポートを確認できます。

### 特定のテストの実行

```bash
# 特定のファイルのテストを実行
pnpm test src/tests/components/Header.test.tsx

# 特定のテスト名でフィルタリング
pnpm test -- -t "正しくレンダリングされること"

# 特定のディレクトリ内のすべてのテストを実行
pnpm test src/tests/utils
```

### デバッグモードでのテスト実行

```bash
# Node.jsインスペクタを有効にしてテストを実行
node --inspect-brk ./node_modules/.bin/jest --runInBand
```

VSCodeでデバッグする場合は、`.vscode/launch.json` に以下の設定を追加します：

```json
{
  "version": "0.2.0",
  "configurations": [
    {
      "type": "node",
      "request": "launch",
      "name": "Jest Current File",
      "program": "${workspaceFolder}/node_modules/.bin/jest",
      "args": [
        "${fileBasename}",
        "--config",
        "jest.config.js"
      ],
      "console": "integratedTerminal",
      "internalConsoleOptions": "neverOpen",
      "disableOptimisticBPs": true
    }
  ]
}
```

## テスト作成ガイド

### 新しいテストファイルの作成

テストファイルは以下のディレクトリ構造に従って配置します：

```
src/
  tests/
    components/     # UIコンポーネントのテスト
    utils/          # ユーティリティ関数のテスト
    integration/    # 統合テスト
```

新しいコンポーネントや機能を追加した場合は、対応するテストファイルを作成してください。

### テストファイルの命名規則

- コンポーネントテスト: `ComponentName.test.tsx`
- ユーティリティ関数テスト: `utilityName.test.ts`
- 統合テスト: `featureName.integration.test.tsx`

### テスト実装のベストプラクティス

1. **テストの独立性を保つ**：各テストは他のテストに依存せず、単独で実行できるようにする
2. **セットアップとクリーンアップ**：`beforeEach`と`afterEach`を適切に使用する
3. **モックの活用**：外部依存を持つコードはモックを使用してテストする
4. **エラーケースのテスト**：正常系だけでなく異常系もテストする
5. **境界値のテスト**：入力値の境界条件をテストする

## トラブルシューティング

### よくある問題と解決策

1. **テストが突然失敗する場合**
   - `node_modules/.cache`を削除してみる
   - Jestをクリーンインストールする: `pnpm remove jest && pnpm install -D jest`

2. **モックが機能しない場合**
   - Jestの設定でモックパスが正しいか確認する
   - 手動モックが正しい場所に配置されているか確認する

3. **テストの実行が遅い場合**
   - 特定のテストに絞って実行する
   - `--maxWorkers=50%`オプションを使用してワーカー数を制限する

4. **スナップショットテストが常に失敗する場合**
   - UIコンポーネントが頻繁に変更される場合は、スナップショットテストの代わりにより具体的なアサーションを使用する
   - `-u`オプションでスナップショットを更新する
