# nogatari manual

- syntax 文法  
  
compiler  
↓  
  
- publish 出力ファイル  

# syntax

オプション@キャラ名{この状態から}->{この状態に移動}  

\#\# scene1  
PLACE@裏山の入り口  

BGM@BGM2  
BGM@path/BGM2.mp3  

@nobita「こんにちは」  
笑顔1@nobita「こんにちは」  
@sizuka「おはようございます」  
@sizuka{ time:1000 }  
笑顔1:@sizuka  

SOUND@baban  
SOUND@path/baban.wav  

@gian「のびたー！」  
@gian->{x:100,y:100,z:100}  
\# gianをx100,y100,z100に一瞬で移動させる。  
@gian{ time:1000 }->{x:100,y:100,z:100}  
\# gianを1000msかけてx100,y100,z100に移動させる。  


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

