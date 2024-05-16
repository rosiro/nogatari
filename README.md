- 2024/5/17 masterブランチの内容を整理整頓してdraft_01を作ることにした。

# nogatari
nogatari is novel game open source format and engine.

## nogarari（のがたり）の目標、特徴
既存のノベルゲームエンジン（スクリプト）はとにかくデバッグが大変だった（～～記法から出力後、どのようになっているかブラックボックスだった。

記法はオープン担っているけど、変換後がよくわからないので、スクリプトから、～～記法のテキストを出力したりした後のテストがむずかしかった問題。  文章量や分岐が増えてくればデバッグが本当に大変

物語を記述するフォーマットが欲しかった（日本語だと多様すぎる）   

- nogatariは基本的にjsonデータ。 
- nogatari記法（人が書きやすい記法 ここからjsonに出力できる）
- ビューア（jsonを解釈して表示する）コード

目標

- 人間がセリフ、ポーズ、出現などをかんたんにかけるようにする。
- 3D,2D,動作環境を問わず演出できるものを目指す。
- nogatariコンパイラが最終的なフォーマットへ変換する
- ビューアで進行を閲覧できるようにする
- テストスクリプト
- とりあえずjavascriptやunityなどで実行できるビューアを作る
- vscodeなどで簡単にかけるようにする
  

