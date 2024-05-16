# 仕様書

nogatariの仕様、nogatariは基本的にjsonデータである。
ゲームで利用する場合にはcompilerによってゲームエンジンや言語で動作するような形に変換するコンパイラによって行う。
大きく分けると以下のカテゴリで分ける

- キャラクター (Characters)
- セリフ (Dialogues)
- シーン (Scenes)
- オーディオ (Audio)


## キャラクター (Characters)
各キャラクターはユニークなIDで識別されます。 
```
{
  "characters": {
    "char_001": {
      "name": "Alice",
      "images": {
        "normal": "images/alice_normal.png",
        "happy": "images/alice_happy.png",
        "sad": "images/alice_sad.png"
      }
    },
    "char_002": {
      "name": "Bob",
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
各セリフはユニークなIDで識別され、話すキャラクターのIDとテキストを含みます。 

```
{
  "dialogues": {
    "dlg_001": {
      "character_id": "char_001",
      "text": "こんにちは、ボブ。今日はどうしたの？"
    },
    "dlg_002": {
      "character_id": "char_002",
      "text": "やあ、アリス。ちょっと相談があるんだ。"
    }
  }
}
```

## シーン (Scenes)
各シーンはユニークなIDで識別され、背景画像、場所、時間、およびそのシーンのセリフのIDを含みます。

```
{
  "scenes": {
    "scene_001": {
      "background": "images/park.png",
      "location": "公園",
      "time": "2024年5月16日 午後3時",
      "dialogues": ["dlg_001", "dlg_002"]
    },
    "scene_002": {
      "background": "images/cafe.png",
      "location": "カフェ",
      "time": "2024年5月16日 午後4時",
      "dialogues": ["dlg_003", "dlg_004"]
    }
  }
}
```

## オーディオ (Audio)
BGMおよび効果音はユニークなIDで識別され、ファイルパスを含みます。

```
{
  "audio": {
    "bgm": {
      "bgm_001": {
        "file": "audio/background_music.mp3"
      }
    },
    "sfx": {
      "sfx_001": {
        "file": "audio/click_sound.mp3"
      },
      "sfx_002": {
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
  "characters": {
    "char_001": {
      "name": "Alice",
      "images": {
        "normal": "images/alice_normal.png",
        "happy": "images/alice_happy.png",
        "sad": "images/alice_sad.png"
      }
    },
    "char_002": {
      "name": "Bob",
      "images": {
        "normal": "images/bob_normal.png",
        "angry": "images/bob_angry.png",
        "surprised": "images/bob_surprised.png"
      }
    }
  },
  "dialogues": {
    "dlg_001": {
      "character_id": "char_001",
      "text": "こんにちは、ボブ。今日はどうしたの？"
    },
    "dlg_002": {
      "character_id": "char_002",
      "text": "やあ、アリス。ちょっと相談があるんだ。"
    }
  },
  "scenes": {
    "scene_001": {
      "background": "images/park.png",
      "location": "公園",
      "time": "2024年5月16日 午後3時",
      "dialogues": ["dlg_001", "dlg_002"]
    },
    "scene_002": {
      "background": "images/cafe.png",
      "location": "カフェ",
      "time": "2024年5月16日 午後4時",
      "dialogues": ["dlg_003", "dlg_004"]
    }
  },
  "audio": {
    "bgm": {
      "bgm_001": {
        "file": "audio/background_music.mp3"
      }
    },
    "sfx": {
      "sfx_001": {
        "file": "audio/click_sound.mp3"
      },
      "sfx_002": {
        "file": "audio/door_sound.mp3"
      }
    }
  }
}
```
