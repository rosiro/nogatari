# nogatari manual

- syntax 文法（シナリオ担当者）  
  
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

## キャラ編
オプション@キャラ名{この状態から}->{この状態に移動}  

@nobita「こんにちは」  
笑顔1@nobita「こんにちは」  
@sizuka「おはようございます」  
無表情@sizuka{ time:1000 }  
笑顔2@sizuka{ time:1000 }  
笑顔1_着物1@sizuka  

@gian「のびたー！」  

@gian->{x:100,y:100,z:100}  
\# gianをx100,y100,z100に一瞬で移動させる。  

@gian{ time:1000 }->{x:100,y:100,z:100}  
\# 1000ms後にgianをx100,y100,z100に移動させる。  

@gian->{x:100,y:100,z:100, time:1000 }  
\# gianをx100,y100,z100に1000msかけて移動させる。  

CHARACTERHIDE@sizuka  
\# 消える



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

### シーンの移動
SCENE@{ time:10000 }->SCENE2
\# 10秒後SCENE2に移動   

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

