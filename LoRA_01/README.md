# このフォルダのプログラムについて

このフォルダのmainプログラム(main.ipynb)は、LoRAの勉強や理解を兼ねて、シンプルな画像分類タスクのニューラルネットワークモデルに対してLoRAを実装して、LoRAの有無の違いを調べてみたものになります。


## 概要

![図1](./work/slide_01.png)

![図2](./work/slide_02.png)

![図3](./work/slide_03.png)

![図4](./work/slide_04.png)

![図5](./work/slide_05.png)

## 詳細

作成予定

main.ipynbで実装しているクラスや関数は下記になります。<br>

1. 関数scaling_per_feature<br>&nbsp;⇒データを各特徴量毎にスケーリング(正規化)するための関数。関数data_preprocessから呼ばれる。
2. クラスMyDataset<br>&nbsp;⇒入力データをデータセットに変換するためのクラス。関数data_preprocessでインスタンス化されて用いる。
3. 関数data_preprocess<br>&nbsp;⇒入力データを前処理するための関数。
4. クラスMyPositionalEncoding<br>&nbsp;⇒Positional Encodingを行うためのクラス。クラスMyTransformerでインスタンス化されて用いる。
5. クラスMyTransformer<br>&nbsp;⇒Transformerモデルを作るためのクラス。
6. 関数rmspe<br>&nbsp;⇒評価関数RMSPEの値を求めるための関数

実装したTransformerモデルのEncoder側の入力の特徴量は「価格」と「数量」の2つで、Decoder側の入力の特徴量は「価格」の1つになります。

## 所感

題材にも寄るのかもしれないけれど、LoRAによって全体の精度そのものが向上するよりかは、狙ったクラスの精度は向上しつつも全体の精度はあまり変わらないのかもしれない。<br>
画像生成で、LoRAによって狙った画像をモデルに容易に生成出来るようにするというのは、応用として確かにと思った。
