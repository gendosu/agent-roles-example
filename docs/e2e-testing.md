# E2Eテスト方針と実行ガイド

このドキュメントでは、計算練習アプリのテスト方針と実行方法について説明します。

## テスト方法

playwright MCP Serverで実行する

## テストの流れ

### playwrightでnavigateにてアクセス

### 初回、データがないので、以下のlocalstorageデータを投入する

- battleStats
  ```
  {"totalBattles":15,"victories":15,"defeats":0,"totalQuestions":23,"correctAnswers":23,"questionStats":{"single_digit_addition":{"total":23,"correct":23,"avgTime":3168.608695652174,"fastestTime":2313}},"magicUsage":{"fire-ball":{"usageCount":23,"successCount":23,"criticalHits":23}},"monsterDefeats":{"m-1-2":14,"m-1-1":1},"dailyStats":{"2025-05-23":{"battles":15,"victories":15,"questions":23,"correct":23,"operatorStats":{"+":{"total":4,"correct":4,"avgTime":3800.75}}}},"lastUpdated":1748041504472}
  ```
- gameSettings
  ```
  {"sound":{"bgmVolume":0.5,"sfxVolume":0.7,"bgmEnabled":true,"sfxEnabled":true},"display":{"animationsEnabled":true,"textSpeed":"normal","useHiragana":false},"difficulty":{"adaptiveDifficulty":true,"timeLimit":15},"autoSaveEnabled":true,"lastUpdated":1747993170553}
  ```
- playerData
  ```
  {"id":"b69d4468-2bbe-45ae-9e5d-e5e32b07ab33","name":"ゆうしゃ","level":7,"exp":1500,"currentHp":35,"maxHp":35,"attack":10,"defense":5,"nextLevelExp":1750,"currentGrade":1,"unlockedSpells":["fire-ball"],"spellLevels":{"fire-ball":1},"activeSpellId":"fire-ball","currentMp":0,"maxMp":0,"speed":10,"intelligence":10,"expHistory":[],"wins":0,"losses":0,"battles":0,"monstersDefeated":{},"criticalRate":0,"learnedMagics":[{"id":"fire-ball","name":"ファイアボール","element":"fire","description":"炎の玉を敵に放つ初級魔法。一桁の足し算で攻撃力が決まる。","power":10,"level":1,"mpCost":5,"targetType":"single","unlockGrade":1,"unlockStage":1001,"operator":"+","questionType":"single_digit_addition","visualEffect":"fire-ball-effect","soundEffect":"/sounds/fire-spell.mp3","imagePath":"/images/spells/fire-ball.png"}],"unlearnedMagics":[],"growthData":{"levelTransition":[],"responseTimeImprovement":[],"correctRateChange":[]},"lastSaved":1748041506482}
  ```
- playerProgress
  ```
  {"clearedStages":{"1001":{"stars":3,"bestScore":100,"completionTime":7.076,"lastPlayedAt":1747978368355},"1002":{"stars":2,"bestScore":100,"completionTime":22.679,"lastPlayedAt":1748041506483}},"unlockedDifficulties":{"1":["beginner","intermediate"],"2":["beginner"],"3":["beginner"],"4":["beginner"],"5":["beginner"],"6":["beginner"]},"rpgProgress":{"clearedBosses":[],"storyFlags":{"stage_1_story_viewed":false},"lastDefeatedSequentialMonsterId":"m-1-2"},"lastUpdated":1748041506485}
  ```
- selectedDifficulty
  ```
  beginner
  ```
- selectedGrade
  ```
  1
  ```