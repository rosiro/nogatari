# nogatari manual

## 流れ
 1. setting.txt 設定ファイル読みお込み 
 2. setting.txt 設定ファイルに記載されたデータの読み込み
 3. global.txt グローバルデータ他ファイル読み込み global変数に
 4. scenario.txt シナリオデータ読み込み
 5. global変数の現在時間から読み込むファイルを選択してファイルを開いてデータを読み込む
 6. 背景を表示
 7. キャラクターを表示
 8. オブジェクトを表示
 9. 該当シナリオファイルデータを順番に表示

## setting.txt
設定ファイル 
~~~
{
  "settings" : {
    "path" : {
      "scenario": "directory",
      "images": "directory",
      "music": "directory",
    },
    "global": {
      "global_file": "global.txt", // セーブデータ、現在の状態
    },
    "scenario": {
      "scenario_file": "scenario.txt",
    }
  }
}
~~~

## state 状態
 global変数的な扱い。セーブされるデータ。ロードされるデータ。
 
 - 背景画像 background-image
 - 画面に登場するキャラクター
 - 画面に表示されるオブジェクト
 - 音楽
 - 現在時間
 - シナリオデータディレクトリ

## シナリオまとめデータ
シナリオデータファイル（複数）
シナリオデータディレクトリにあるファイルを読み込み

- シナリオ設定ファイルscenario.txt
- 

```
### scenario.txt
{
    scenarios: [
      { "filename" : "aaa.txt", "start_time" : timestamp, "end_time" : timestamp  },
      { "filename" : "aaa.txt", "start_time" : timestamp, "end_time" : timestamp  },
     
    ]
}
```
### シナリオデータ
aaa.txt
```
{
    "events" : [
        {
            "comment": "背景変更",
            "background" : "background.png,
            "time": timestamp,
        },
        {
            "comment": "キャラクター表示",
            "character": "nobita",
            "speech": "hello hello hello world",
            "time": timestamp,
        },
        {
            "comment": "キャラクターのアニメーションステート切り替え",
            "character": "nobita",
            "animation_state": "walk",
            "time": timestamp,
        },
    ]    
}
```

## syntax 文法（シナリオ担当者）  

  compiler(nogatari compiler)  
  ↓  
  
- publish 出力ファイル  
- game engine import   


# MEMO
- Q いちいちコンパイルが面倒だよ！
- A 出力ファイル(JSON)を直接いじる（なんとなくわかる）

- Q nogatari記法中にユーザ独自の命令を記述できるようにしたい  
- A そうできるようにしたい　{def：左}{x:100,y:100,z:100}　←みたいに  

# nogatari記法
## 誰 キャラクター
nobita@doraemons.jp

nobitaはキャラクター名
doraemonsは所属グループ名
jpは所属グループ名

## 話す(行動)
nobita@doraemons.jp [こんにちは@jp] [hello world@en]



@gian「のびたー！」  

@gian->{x:100,y:100,z:100}  
\# gianをx100,y100,z100に一瞬で移動させる。  

@gian{ time:1000 }->{x:100,y:100,z:100}  
\# 1000ms後にgianをx100,y100,z100に移動させる。  

@gian->{x:100,y:100,z:100, time:1000 }  
\# gianをx100,y100,z100に1000msかけて移動させる。  

CHARACTERHIDE@sizuka  
\# 消える

STARE(sizuka)@gian  
gianがsizukaを見つめる


## 場面変更、画像
\#\# scene1  
PLACE@裏山の入り口  

## 音楽、効果音

BGM@BGM2  
BGM@path/BGM2.mp3  
SOUND@baban  
SOUND@path/baban.wav  

## 演出

ANIME:SHAKE@nobita  
ANIME:SHAKE@背景  
ANIME:FADEOUT@CHARA_MOVE_DEFAULT  # デフォルトのキャラ移動時のアニメーションを設定  
ANIME:FADEOUT@CHARA_SPEAK_AFTER_DEFAULT  # デフォルトのキャラ会話後のアニメーションを設定  

シーンの移動  
SCENE@{ time:10000 }->SCENE2
\# 10秒後SCENE2に移動   

1000@WAIT
\# 1000msシーンを停止する

## SYSTEM
### 変数
$変数名 = 値  

### IF
### FOR 

# publish
出力するファイルフォーマット  
## ファイルが最新かどうかを確認キャッシュ
1. settings.jsonのversionを確認
1. directorファイル、actorsファイル、sceneファイルのファイルを確認
1. director.jsonのversionを確認 
1. actors.jsonのversionを確認 
1. places.jsonのversionを確認 
1. scene.jsonのversionを確認 

## setings 設定
設定ファイル
settings.json  

## director シーンのまとめ
複数のシーンの関係をまとめるファイル
director.json  

## actors
俳優ファイル　キャラクター設定ファイル
actors.json  

## places
場所ファイル　場所や画像
places.json  

## scene シーン
個々のシーン、セリフ、背景など

