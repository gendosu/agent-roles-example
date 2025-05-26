# 概要

このドキュメントは、計算練習アプリを作成するプロジェクトの概念と目的について説明します。現在は、RPG（ロールプレイングゲーム）形式の計算ドリルとして拡張開発を進めています。

## 目的

このツールは、小学生の計算能力向上を目的として、計算をゲームとして楽しめて、かつゲーミフィケーションを取り入れたアプリの構築を目指します。RPG版では、計算問題を解くという学習活動をRPGの戦闘システムと組み合わせ、より楽しく、魅力的な学習体験を提供します。

## RPG版コンセプト

「計算RPG」は、プレイヤーが勇者となって、学年別・難易度別のモンスターと戦いながら計算力を鍛えるゲームです。プレイヤーの攻撃は、計算問題に正解することで発動します。正解率や解答速度によって攻撃力が変わり、より正確に素早く解けるほど強力な攻撃ができます。

主な特徴：
- プレイヤーキャラクターとモンスターによる戦闘システム
- 学年別・難易度別のモンスターと問題設定
- 計算タイプに対応した魔法攻撃システム
- レベルアップと成長要素
- 戦闘アニメーションと視覚効果

## プロジェクトについて

- 開発言語: TypeScript
- フレームワーク: next.js
- パッケージ管理: pnpm
  - npmコマンドの実行、パッケージのインストールをするときにはpnpmコマンドを使用する

## Project Structure

```
calc-app3/
├── index.md
├── jest.config.js
├── jest.setup.js
├── next-env.d.ts
├── next.config.js
├── package.json
├── playwright.config.ts
├── pnpm-lock.yaml
├── postcss.config.js
├── tailwind.config.js
├── TODO_ARCHIVE.md
├── TODO.md
├── tsconfig.json
├── 議事録_ステージ制タスク化.md
├── 魔法レベルアップシステム設計.md
├── docs/                       # プロジェクトドキュメント
│   ├── description.md          # プロジェクト概要
│   ├── e2e-testing.md
│   ├── general-rules.md        # 一般ルール
│   ├── index.md               # ドキュメント目次
│   ├── test-execution-guide.md # テスト実行ガイド
│   └── testing.md             # テスト関連文書
├── e2e/                       # E2Eテスト
│   └── sequential-battle.spec.ts # 連続バトルテスト
├── public/                   # 静的ファイル
│   └── images/              # 画像ファイル
│       ├── spells/          # 魔法エフェクト画像
│       │   ├── earth-quake.png
│       │   ├── fire-ball.png
│       │   ├── heal-light.png
│       │   ├── ice-arrow.png
│       │   └── thunder-bolt.png
│       ├── tiles/           # タイル画像
│       ├── bundan_commander.png
│       ├── bundan_king.png
│       ├── bundan_medium.png
│       ├── bundan_small.png
│       ├── bundan_workshop.png
│       ├── dokusen_commander.png
│       ├── dokusen_king.png
│       ├── dokusen_medium.png
│       ├── dokusen_small.png
│       ├── dokusen_strong.png
│       ├── konton_admiral.png
│       ├── konton_king.png
│       ├── konton_large.png
│       ├── konton_medium.png
│       ├── konton_small.png
│       ├── muchitsujo_emperor.png
│       ├── muchitsujo_engineer.png
│       ├── muchitsujo_large.png
│       ├── muchitsujo_medium.png
│       ├── muchitsujo_small.png
│       ├── musabori_general.png
│       ├── musabori_king.png
│       ├── musabori_large.png
│       ├── musabori_medium.png
│       ├── musabori_small.png
│       ├── player.png
│       ├── wasurenbo_flower.png
│       ├── wasurenbo_forest.png
│       ├── wasurenbo_king.png
│       ├── wasurenbo_small.png
│       └── wasurenbo_water.png
├── screenshots/             # スクリーンショット
├── src/                       # ソースコード
│   ├── test-fraction-display.js
│   ├── app/                   # Next.js App Router
│   │   ├── battle/           # バトル画面
│   │   │   ├── page.tsx
│   │   │   └── start/
│   │   │       └── page.tsx
│   │   ├── free-mode/        # フリーモード
│   │   ├── legacy/           # レガシー画面
│   │   ├── menu/             # メニュー画面
│   │   │   └── page.tsx
│   │   ├── settings/         # 設定画面
│   │   │   └── page.tsx
│   │   ├── stages/           # ステージ選択画面
│   │   │   └── page.tsx
│   │   ├── stats/            # 統計画面
│   │   ├── globals.css       # グローバルスタイル
│   │   ├── layout.tsx        # レイアウトコンポーネント
│   │   └── page.tsx          # ホーム画面
│   ├── components/           # Reactコンポーネント
│   │   ├── __tests__/        # コンポーネントテスト
│   │   │   └── BattleScreen.test.tsx
│   │   ├── charts/           # チャート関連コンポーネント
│   │   │   ├── GradeProgressChart.tsx
│   │   │   ├── GrowthChart.tsx
│   │   │   ├── StatsTabs.tsx
│   │   │   ├── SubjectPerformanceChart.tsx
│   │   │   └── TimeProgressChart.tsx
│   │   ├── AnswerInput.tsx
│   │   ├── BattleScreen.tsx
│   │   ├── CharacterBasicInfo.tsx
│   │   ├── CharacterExperience.tsx
│   │   ├── CharacterStats.tsx
│   │   ├── DifficultyTabs.tsx
│   │   ├── Dpad.tsx
│   │   ├── GradeSelector.tsx
│   │   ├── Header.tsx
│   │   ├── HealthBar.tsx
│   │   ├── index.ts          # コンポーネントエクスポート
│   │   ├── Keypad.tsx
│   │   ├── MagicCard.tsx
│   │   ├── MagicSelector.tsx
│   │   ├── MagicUsageHistory.tsx
│   │   ├── MonsterGroupDisplay.tsx
│   │   ├── PhaserGame.tsx
│   │   ├── QuestionDisplay.tsx
│   │   ├── ResultDisplay.tsx
│   │   ├── StageCard.tsx
│   │   ├── StageGame.tsx
│   │   ├── StageList.tsx
│   │   ├── StatusBar.tsx
│   │   └── StoryModal.tsx
│   ├── constants/            # 定数定義
│   │   ├── index.ts          # 一般定数
│   │   ├── magic.ts          # 魔法関連定数
│   │   ├── rpgData.ts        # RPGデータ
│   │   ├── stages.ts         # ステージ定数
│   │   └── storyData.ts      # ストーリーデータ
│   ├── types/                # TypeScript型定義
│   │   ├── index.ts          # 一般型定義
│   │   ├── magic.ts          # 魔法関連型
│   │   ├── rpg.ts            # RPG関連型
│   │   ├── stage.ts          # ステージ関連型
│   │   └── storage.ts        # ストレージ関連型
│   └── utils/                # ユーティリティ関数
│       ├── __tests__/        # ユーティリティテスト
│       │   ├── characterManager.test.ts
│       │   ├── dataAccessLayer.test.ts
│       │   ├── progressManager.test.ts
│       │   ├── questionGenerator.test.ts
│       │   └── storageManager.test.ts
│       ├── battleStatsUtils.ts
│       ├── characterManager.ts
│       ├── cleanupUtils.ts
│       ├── dataAccessLayer.ts
│       ├── expCalculator.ts
│       ├── mathUtils.ts
│       ├── progressManager.ts
│       ├── questionGenerator.ts
│       ├── rpgUtils.ts
│       ├── stageQuestionGenerator.ts
│       ├── statsUtils.ts
│       ├── storageManager.ts
│       └── textConverter.ts
├── 資料/                   # 設計資料・仕様書
│   ├── MP設計.md
│   ├── RPG版計算ドリルの設計.md
│   ├── キャラクタープロンプトテンプレート.md
│   ├── キャラクター設定.md
│   ├── ゲームシステム設計.md
│   ├── ステージ制の設計.md
│   ├── データ保存アーキテクチャ設計.md
│   ├── パフォーマンス調査_元タスク.md
│   ├── フィールドタイル生成プロンプト.md
│   ├── 仕様再検討_学年別難易度調整調査.md
│   ├── 実績グラフ化の設計.md
│   ├── 小学校算数教育概要.md
│   └── ストーリー/          # ストーリー関連資料
│       ├── 1年生.md
│       ├── 2年生.md
│       ├── 3年生.md
│       ├── 4年生.md
│       ├── 5年生.md
│       ├── 6年生.md
│       └── 概要.md
└── 設定ファイル類
    ├── package.json
    ├── next.config.js
    ├── tailwind.config.js
    ├── jest.config.js
    ├── playwright.config.ts
    └── tsconfig.json
```
> 注: `result/`、`temp/`、`node_modules`、`.next`ディレクトリには動的に生成されるファイルが含まれるため、メンテナンス時のディレクトリ構造確認では無視してください。
