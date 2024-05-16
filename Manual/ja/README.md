# 仕様書

nogatariの仕様、nogatariは基本的にjsonデータである。
ゲームで利用する場合にはcompilerによってゲームエンジンや言語で動作するような形に変換するコンパイラによって行う。
大きく分けると以下のカテゴリで分ける

- システム ( Systems )
- キャラクター (Characters)
- セリフ (Dialogues)
- シーン (Scenes)
- オーディオ (Audio)

## システム (System)
ゲームの基本的な設定を含みます。 

- title: ゲームのタイトル。
- version: ゲームのバージョン番号。
- language: ゲームのデフォルト言語。ISO 639-1形式の言語コード（例：jaは日本語、enは英語）。
- timezone: ゲームが使用するタイムゾーン（例：Asia/Tokyo）。
- utf: 使用する文字エンコーディング（例：UTF-8）。
- gmt: ゲームが使用するタイムゾーンのGMTオフセット（例：+09:00）。
- base_path: ゲームリソースの基礎パス。このパスを基に画像や音声ファイルなどのリソースを参照します。


```
{
  "system": {
    "title": "Adventure Game",
    "version": "1.0.0",
    "language": "ja",
    "timezone": "Asia/Tokyo",
    "utf": "UTF-8",
    "gmt": "+09:00",
    "base_path": "/game/assets/"
  }
}
```


## キャラクター (Characters)
各キャラクターはユニークなIDで識別されます。 

- id: キャラクターのユニークな識別子。
- name: キャラクターの名前。各言語ごとに設定できます（例：jaは日本語、enは英語）。
- images: キャラクターの画像パス。表情やポーズごとに設定できます。

```
{
  "characters": {
    "char_001": {
      "name": {
        "ja": "アリス",
        "en": "Alice"
      },
      "images": {
        "normal": "images/alice_normal.png",
        "happy": "images/alice_happy.png",
        "sad": "images/alice_sad.png"
      }
    },
    "char_002": {
      "name": {
        "ja": "ボブ",
        "en": "Bob"
      },
      "images": {
        "normal": "images/bob_normal.png",
        "angry": "images/bob_angry.png",
        "surprised": "images/bob_surprised.png"
      }
    }
  }
}

```

## セリフ (Dialogues)
各セリフはユニークなIDで識別され、話すキャラクターのID、テキスト、およびタイムスタンプを含みます。テキストは多言語対応です。 

- id: セリフのユニークな識別子。
- character_id: 話すキャラクターのID。
- text: セリフの内容。各言語ごとに設定できます（例：jaは日本語、enは英語）。
- timestamp: セリフのタイムスタンプ（Unixタイムスタンプ形式）。

 
```
{
  "dialogues": {
    "dlg_001": {
      "id": "dlg_001",
      "character_id": "char_001",
      "text": {
        "ja": "こんにちは、ボブ。今日はどうしたの？",
        "en": "Hello, Bob. What's up today?"
      },
      "timestamp": 1684287600
    },
    "dlg_002": {
      "id": "dlg_002",
      "character_id": "char_002",
      "text": {
        "ja": "やあ、アリス。ちょっと相談があるんだ。",
        "en": "Hi, Alice. I have something to talk about."
      },
      "timestamp": 1684288200
    }
  }
}

```

## シーン (Scenes)
各シーンはユニークなIDで識別され、背景画像、場所、時間、およびそのシーンのセリフのIDを含みます。

- id: シーンのユニークな識別子。
- background: 背景画像のパス。
- location: シーンの場所の名前。
- time: シーンの時間（ISO 8601形式）。
- dialogues: シーン内のセリフのIDリスト。

```
{
  "scenes": {
    "scene_001": {
      "id": "scene_001",
      "background": "images/park.png",
      "location": "Park",
      "time": "2024-05-16T15:00:00Z",
      "dialogues": ["dlg_001", "dlg_002"]
    },
    "scene_002": {
      "id": "scene_002",
      "background": "images/cafe.png",
      "location": "Cafe",
      "time": "2024-05-16T16:00:00Z",
      "dialogues": ["dlg_003", "dlg_004"]
    }
  }
}

```

## オーディオ (Audio)
BGMおよび効果音はユニークなIDで識別され、ファイルパスを含みます。

- id: オーディオファイルのユニークな識別子。
- file: オーディオファイルのパス。

```
{
  "audio": {
    "bgm": {
      "bgm_001": {
        "id": "bgm_001",
        "file": "audio/background_music.mp3"
      }
    },
    "sfx": {
      "sfx_001": {
        "id": "sfx_001",
        "file": "audio/click_sound.mp3"
      },
      "sfx_002": {
        "id": "sfx_002",
        "file": "audio/door_sound.mp3"
      }
    }
  }
}


```

## json サンプル
以下は、すべての要素をまとめたJSONの例です。 

```
{
  "system": {
    "title": "Adventure Game",
    "version": "1.0.0",
    "language": "ja",
    "timezone": "Asia/Tokyo",
    "utf": "UTF-8",
    "gmt": "+09:00",
    "base_path": "/game/assets/"
  },
  "characters": {
    "char_001": {
      "name": {
        "ja": "アリス",
        "en": "Alice"
      },
      "images": {
        "normal": "images/alice_normal.png",
        "happy": "images/alice_happy.png",
        "sad": "images/alice_sad.png"
      }
    },
    "char_002": {
      "name": {
        "ja": "ボブ",
        "en": "Bob"
      },
      "images": {
        "normal": "images/bob_normal.png",
        "angry": "images/bob_angry.png",
        "surprised": "images/bob_surprised.png"
      }
    }
  },
  "dialogues": {
    "dlg_001": {
      "id": "dlg_001",
      "character_id": "char_001",
      "text": {
        "ja": "こんにちは、ボブ。今日はどうしたの？",
        "en": "Hello, Bob. What's up today?"
      },
      "timestamp": 1684287600
    },
    "dlg_002": {
      "id": "dlg_002",
      "character_id": "char_002",
      "text": {
        "ja": "やあ、アリス。ちょっと相談があるんだ。",
        "en": "Hi, Alice. I have something to talk about."
      },
      "timestamp": 1684288200
    }
  },
  "scenes": {
    "scene_001": {
      "id": "scene_001",
      "background": "images/park.png",
      "location": "Park",
      "time": "2024-05-16T15:00:00Z",
      "dialogues": ["dlg_001", "dlg_002"]
    },
    "scene_002": {
      "id": "scene_002",
      "background": "images/cafe.png",
      "location": "Cafe",
      "time": "2024-05-16T16:00:00Z",
      "dialogues": ["dlg_003", "dlg_004"]
    }
  },
  "audio": {
    "bgm": {
      "bgm_001": {
        "id": "bgm_001",
        "file": "audio/background_music.mp3"
      }
    },
    "sfx": {
      "sfx_001": {
        "id": "sfx_001",
        "file": "audio/click_sound.mp3"
      },
      "sfx_002": {
        "id": "sfx_002",
        "file": "audio/door_sound.mp3"
      }
    }
  }
}

```
