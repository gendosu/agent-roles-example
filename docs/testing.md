# テスト方針と実行ガイド

このドキュメントでは、計算練習アプリのテスト方針と実行方法について説明します。

## テスト方針

### 1. テストの種類

当プロジェクトでは以下の種類のテストを実施します：

1. **ユニットテスト**：個々の関数やコンポーネントの機能を検証
   - 数学関連のユーティリティ関数
   - ステート管理関数
   - UIコンポーネント（単体）

2. **統合テスト**：複数のコンポーネントやモジュールの連携を検証
   - フォーム操作と状態更新
   - データフローの検証

3. **スナップショットテスト**：UIコンポーネントの表示が意図通りであることを検証

### 2. テスト対象の優先順位

1. **最優先**：ビジネスロジックを含むモジュール
   - 計算問題の生成ロジック
   - 採点ロジック
   - 進捗管理ロジック

2. **高優先度**：ユーザー入力を処理するコンポーネント
   - 回答入力フォーム
   - 設定変更機能

3. **標準優先度**：表示用コンポーネント
   - 結果表示
   - 統計情報表示

### 3. テストカバレッジ目標

- **全体カバレッジ目標**: 80%以上
- **ビジネスロジック**: 90%以上
- **UIコンポーネント**: 70%以上

### 4. テストファイル配置方針

テストファイルは`src/tests`ディレクトリに集約して配置します。

```
src/
  tests/
    components/     # UIコンポーネントのテスト
    utils/          # ユーティリティ関数のテスト
    integration/    # 統合テスト
```

## テスト実行方法

### 基本的なテスト実行

```bash
# すべてのテストを実行
pnpm test

# 監視モードでテストを実行（ファイル変更を検知して自動実行）
pnpm test:watch

# テストカバレッジレポートを生成
pnpm test:coverage
```

### 特定のテストファイルの実行

```bash
# 特定のファイルのテストを実行
pnpm test src/tests/components/Header.test.tsx

# 特定のパターンに一致するテストを実行
pnpm test -- -t "Headerコンポーネント"
```

### テストのデバッグ

VSCodeでテストをデバッグするには：

1. VSCodeのデバッグビューを開く
2. 「構成を追加」から「Jest」を選択
3. デバッグしたいテストファイルで中断点を設定
4. デバッグセッションを実行

## Gitフック連携

コミット前に自動的にテストが実行されるよう設定されています：

- pre-commitフック: 変更されたファイルに関連するテストを実行
- lint-staged: コミット対象ファイルのリント＆テスト実行

## テスト作成ガイドライン

### コンポーネントテスト

```tsx
import { render, screen } from '@testing-library/react';
import userEvent from '@testing-library/user-event';
import MyComponent from '@/components/MyComponent';

describe('MyComponent', () => {
  it('正しくレンダリングされること', () => {
    render(<MyComponent />);
    expect(screen.getByText('期待するテキスト')).toBeInTheDocument();
  });

  it('ユーザーの操作に正しく反応すること', async () => {
    render(<MyComponent />);
    const button = screen.getByRole('button', { name: 'クリック' });
    await userEvent.click(button);
    expect(screen.getByText('クリック後のテキスト')).toBeInTheDocument();
  });
});
```

### ユーティリティ関数テスト

```tsx
import { myFunction } from '@/utils/myUtils';

describe('myFunction', () => {
  it('正しい結果を返すこと', () => {
    expect(myFunction(1, 2)).toBe(3);
  });

  it('境界条件で正しく動作すること', () => {
    expect(myFunction(0, 0)).toBe(0);
    expect(myFunction(-1, 1)).toBe(0);
  });

  it('無効な入力でエラーをスローすること', () => {
    expect(() => myFunction(null, 2)).toThrow();
  });
});
```
