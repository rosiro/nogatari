# nogatari
nogatari is novel game open source format and engine.

## nogarari（のがたり）の目標、特徴
既存のノベルゲームエンジン（スクリプト）はとにかくデバッグが大変だった（～～記法から出力後、どのようになっているかブラックボックスだった。

記法はオープン担っているけど、変換後がよくわからないので、スクリプトから、～～記法のテキストを出力したりした後のテストがむずかしかった問題。  文章量や分岐が増えてくればデバッグが本当に大変

物語を記述するフォーマットが欲しかった（日本語だと多様すぎる）   

nogatari記法を変換後はjsonにすること。 

- 人間がセリフ、ポーズ、出現などをかんたんにかけるようにする。
- 3D,2D,動作環境を問わず演出できるものを目指す。
- nogatariコンパイラが最終的なフォーマットへ変換する
- 最終的にはJSONまたはMessagePakになる
- 出力されたフォーマットを各ゲームエンジンなどで表現できるようにする 
- ゲームエンジンとは別にビューアが欲しい
- テストスクリプト

## TODO
- 文法  
- 出力フォーマット  
- [マニュアル](/Manual/ja)

## MEMO
- キャラクターのポーズや表情の名前いちいちおぼえてられない（自動補完してほしい）
