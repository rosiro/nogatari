# 仕様書

## 1. System
- **base_path**: アセット（画像や音声ファイルなど）の基本パス。
- **save_data_path**: セーブデータの保存場所。
- **default_bgm**: デフォルトの背景音楽ファイルのパス。
- **languages**: サポートする言語のリスト（例："en", "ja"）。
- **timezone**: 使用するタイムゾーン（例："UTC"）。

## 2. Characters
キャラクターの情報を含むセクション。

- **id**: キャラクターのユニークなID。
- **name**: 各言語ごとのキャラクターの名前。
- **images**: キャラクターの2D画像のリスト。
  - **normal**: 通常の画像パス。
  - **happy**: 喜びの画像パス。
  - **sad**: 悲しみの画像パス。
- **model**: 3Dモデルに関する情報。
  - **file**: 3Dモデルのファイルパス。
  - **animations**: 利用可能なアニメーションのリスト。
    - **idle**: 待機アニメーションのファイルパス。
    - **walk**: 歩行アニメーションのファイルパス。
    - **talk**: 会話アニメーションのファイルパス。

## 3. Scenes
シーンの情報を含むセクション。

- **id**: シーンのユニークなID。
- **background**: シーンの背景画像のパス。
- **location**: 各言語ごとの場所の名前。

## 4. Scenarios
シナリオの情報を含むセクション。

- **id**: シナリオのユニークなID。
- **scene_id**: このシナリオが属するシーンのID。
- **events**: イベントの配列。各イベントは異なるタイプを持ちます。
  - **id**: イベントのユニークなID。
  - **type**: イベントのタイプ（例：`dialogue`、`audio`、`sleep`、`choice`、`animation`、`transition`、`variable`、`effect`）。
  - **character**: `dialogue` イベントにおけるキャラクター情報。
    - **character_id**: キャラクターのID。
    - **showtype**: キャラクターの表示タイプ（`image` または `model`）。
    - **animation**: キャラクターのアニメーションまたは表情。
  - **text**: `dialogue` イベントのテキスト（各言語ごと）。
  - **timestamp**: イベントの発生時刻（Unixタイムスタンプ形式）。
  - **audio_id**: `audio` イベントにおけるオーディオのID。
  - **loop**: `audio` イベントがループするかどうかの設定（`true`/`false`）。
  - **duration**: `sleep` イベントの待機時間（秒単位）。
  - **choices**: `choice` イベントの選択肢のリスト。
    - **text**: 各言語ごとの選択肢のテキスト。
    - **next_scenario_id**: 選択後に進むシナリオのID。
  - **target**: `animation` イベントのターゲット（例：`background`）。
  - **animation_file**: `animation` イベントのアニメーションファイルのパス。
  - **effect**: `transition` イベントのエフェクト（例：`fade_in`）。
  - **variable_name**: `variable` イベントの変数名。
  - **operation**: `variable` イベントの操作（例：`increment`）。
  - **value**: `variable` イベントで操作する値（例：1）。
  - **effect_file**: `effect` イベントのエフェクトファイルのパス。

## 5. Audio
オーディオファイルの情報を含むセクション。

- **bgm**: 背景音楽のリスト。
  - **id**: BGMのユニークなID。
  - **file**: BGMのファイルパス。
  - **loop**: ループするかどうかの設定（`true`/`false`）。
- **sfx**: 効果音のリスト。
  - **id**: 効果音のユニークなID。
  - **file**: 効果音のファイルパス。
  - **loop**: ループするかどうかの設定（`true`/`false`）。

### 仕様例
```json
{
  "system": {
    "base_path": "assets/",
    "save_data_path": "saves/",
    "default_bgm": "audio/default_bgm.mp3",
    "languages": ["en", "ja"],
    "timezone": "UTC"
  },
  "characters": {
    "char_001": {
      "name": {
        "en": "Alice",
        "ja": "アリス"
      },
      "images": {
        "normal": "images/alice_normal.png",
        "happy": "images/alice_happy.png",
        "sad": "images/alice_sad.png"
      },
      "model": {
        "file": "models/alice_model.fbx",
        "animations": {
          "idle": "animations/alice_idle.fbx",
          "walk": "animations/alice_walk.fbx",
          "talk": "animations/alice_talk.fbx"
        }
      }
    },
    "char_002": {
      "name": {
        "en": "Bob",
        "ja": "ボブ"
      },
      "images": {
        "normal": "images/bob_normal.png",
        "angry": "images/bob_angry.png",
        "surprised": "images/bob_surprised.png"
      },
      "model": {
        "file": "models/bob_model.fbx",
        "animations": {
          "idle": "animations/bob_idle.fbx",
          "walk": "animations/bob_walk.fbx",
          "talk": "animations/bob_talk.fbx"
        }
      }
    }
  },
  "scenes": {
    "scene_001": {
      "id": "scene_001",
      "background": "images/park.png",
      "location": {
        "en": "Park",
        "ja": "公園"
      }
    },
    "scene_002": {
      "id": "scene_002",
      "background": "images/cafe.png",
      "location": {
        "en": "Cafe",
        "ja": "カフェ"
      }
    }
  },
  "scenarios": {
    "scenario_001": {
      "id": "scenario_001",
      "scene_id": "scene_001",
      "events": [
        {
          "id": "event_001",
          "type": "dialogue",
          "character": {
            "character_id": "char_001",
            "showtype": "image",
            "animation": "normal"
          },
          "text": {
            "en": "Hello, Bob. What's up today?",
            "ja": "こんにちは、ボブ。今日はどうしたの？"
          },
          "timestamp": 1715865600
        },
        {
          "id": "event_002",
          "type": "audio",
          "audio_id": "sfx_001",
          "loop": false
        },
        {
          "id": "event_003",
          "type": "dialogue",
          "character": {
            "character_id": "char_002",
            "showtype": "image",
            "animation": "normal"
          },
          "text": {
            "en": "Hey, Alice. I have something to talk about.",
            "ja": "やあ、アリス。ちょっと相談があるんだ。"
          },
          "timestamp": 1715865900
        },
        {
          "id": "event_004",
          "type": "sleep",
          "duration": 2
        },
        {
          "id": "event_005",
          "type": "choice",
          "choices": [
            {
              "text": {
                "en": "Yes",
                "ja": "はい"
              },
              "next_scenario_id": "scenario_002"
            },
            {
              "text": {
                "en": "No",
                "ja": "いいえ"
              },
              "next_scenario_id": "scenario_003"
            }
          ]
        },
        {
          "id": "event_006",
          "type": "animation",
          "target": "background",
          "animation_file": "animations/scene_transition.fbx"
        },
        {
          "id": "event_007",
          "type": "transition",
          "effect": "fade_in",
          "duration": 1.5
        },
        {
          "id": "event_008",
          "type": "variable",
          "variable_name": "trust",
          "operation": "increment",
          "value": 1
        },
        {
          "id": "event_009",
          "type": "effect",
          "effect_file": "effects/sparkle.png",
          "duration": 3.0
        }
      ]
    },
    "scenario_002": {
      "id": "scenario_002",
      "scene_id": "scene_002",
      "events": [
        {
          "id": "event_010",
          "type": "dialogue",
          "character": {
            "character_id": "char_001",
            "showtype": "image",
            "animation": "normal"
          },
          "text": {
            "en": "How about a coffee?",
            "ja": "コーヒーはいかがですか？"
          },
          "timestamp": 1715869200
        },
        {
          "id": "event_011",
          "type": "audio",
          "audio_id": "sfx_002",
          "loop": false
        },
        {
          "id": "event_012",
          "type": "dialogue",
          "character": {
            "character_id": "char_002",
            "showtype": "image",
            "animation": "normal"
          },
          "text": {
            "en": "Sure, that sounds great!",
            "ja": "いいね、それは素晴らしいね！"
          },
          "timestamp": 1715869500
        }
      ]
    }
  },
  "audio": {
    "bgm": {
      "bgm_001": {
        "file": "audio/background_music.mp3",
        "loop": true
      }
    },
    "sfx": {
      "sfx_001": {
        "file": "audio/click_sound.mp3",
        "loop": false
      },
      "sfx_002": {
        "file": "audio/door_sound.mp3",
        "loop": false
      }
    }
  }
}
