# scene シーン
シーンのjsonフォーマット

```
{
    "scene-title" : "シーンタイトル",
    "scene" : [
        "show-background" : {
            "path": "background.jpg",
            "animation-type" : "fade-in",
            "animation-time" : 100,
            "animation-wait" : "true"
        },
        "play-music" : {
            "path" : "bgm.mp3",
            "loop" : true
        },
        "stop-music" : {
            "path" : "bgm.mp3"
        },
        "play-sound" : {
            "path" : "sound.wav",
            "finish-wait" : true
        },
        "stop-sound" : {
            "path" : "sound.wav"
        },
        "show-actor" : {
            "actor-name" : "nobita_1",
            "actions" : [
                {
                    "animation-type" : "fade-in",
                    "animation-time" : 100,
                    "animation-wait" : "true",
                }
            ],
        },
        "talk-actor" : {
            "actor-name" : "nobita1",
            "speak" : "こんにちは！"
            "animation-type" : "mojiokuri",
            "animation-time" : 30,
        },
        "move" : {
            "type" : "actor",
            "name" : "nobita1",
            "from" : {
                "x" : 100,
                "y" : 100,
                "z" : 1
            },
            "to : {
                "x" : 120,
                "y" : 120",
                "z" : 1
            },
            "time" : 100
        },
        "hide-actor" : {
            "actor-name" : "nobita1",
            "actions" : [
                {
                    "animation-type" : "fade-in",
                    "animation-time" : 100,
                    "animation-wait" : "true",
                }
            ],
        },
    ]
}
```