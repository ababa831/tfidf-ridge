# tfidf-ridge

<作成中，コード未debug>

テキストデータをTF-IDF（Term Frequency Inverse Document Frequency）値の重みを用いてtokenizeし，Ridge回帰を行う実験用コード．

## モチベーション

テキストデータをone-hot encodingしたり，TF-IDFでベクトル化したりする場合等，スパースなデータを扱うときに線形回帰がよく用いられる．Kaggleでスパースデータを扱うことになりそうなので，この機会にTF-IDFと線形回帰(特にRidge回帰)の基礎を振り返ろうと思った．

## TF-IDFとは？

文書中に含まれる単語の特徴の強さ（重み）を表現する手法の一つ．

- TF 単語出現数 (ある単語が文書内で出現する頻度)
- IDF 逆文書頻度（ある単語がいくつの文書*で使われているかを表す値）

これらの指標を用いて，文章中に含まれる単語の重要度を評価する．

(\*一文書の単位は，どのような文書の単位で特徴分けしたいかによる．)

<br>
TF，IDFがともに大きいとき，

- ある単語が，一つの文書で頻出する
- ある単語が，複数の文書であまり横断的に使われていない

ことを意味し，この場合は重要度が高くなる．

例えば，次のような「アメリカ旅行日記」を考える．

- 各日付の日記を一文書とする．
- 「アメリカ」という単語は出現頻度が高い．
- しかし，文書全てを通して出現する．
- 2/1の日記では，「自由の女神」という単語が頻出する．
- しかし，それ以外の日付では出現しない．

この場合，2/1の文書を特徴付ける単語は「アメリカ」よりも「自由の女神」であってほしい．

逆文書頻度(IDF)を指標とすることで，`頻出の単語＝重要語`とは限らないケースでも，上手く重要度を表現できる．

### 指標の計算式
tf,idfの表現方法は[色々ある](http://yukinoi.hatenablog.com/entry/2016/11/12/231422)が，一番オーソドックスな計算式を以下に示す．



## 線形回帰

### 基本

### Lasso回帰

### Ridge回帰

### Elastic-Net

## 実験用コード

classification.ipynb

- Kaggleの[toxicコンペの文書データ](https://www.kaggle.com/c/jigsaw-toxic-comment-classification-challenge/data)を使用する．
- 文書のクリーニングは，大文字→小文字に変換のみ行う．
- 文書データは，one-hot
- TF-IDFは，scikit learnの`TfidfVectorizer`クラスを使用
- Ridge回帰は，scikit learnの`RidgeClassifier`クラスを使用


### 使い方

1. 本リポジトリをgit cloneする．
2. DLしたリポジトリのディレクトリ内に`train.csv`, `test.csv`, `sample_submission.csv`（文書データ）を置く
3. `$ pip install -r requirements.txt`を実行する．
3. `classification.ipynb`を開き，上から順にセルを実行する．

