# scene シーン
シーンのjsonフォーマット

```
{
    "scene-title" : "シーンタイトル",
    "background" : "background image path",
    "scene" : [
            {
                "show-actor" : {
                             "actor-name" : "nobita_1",
                             "appear-actions" : [
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
            },
    ]
}
```
