# 概要

これは hb-converter の動作確認用の markdown サンプルです．

* 対応しているすべての markdown 構文を内包
* 独自に採用している仕様に合致する記述

という方針のもとに作成されました．


# 様々な markdown 構文

## 見出し

何段階でも処理することができます．

### 細かい見出し

#### さらに細かい見出し

##### もっと細かい見出し

## 引用構文

> ここが引用です  
> 別のものを `include` することもできます  
> 例えば，[tex: \rm\TeX %]の数式やコード `\rm\TeX`  
> あるいはリンク [link](https://gooogle.com) など  
> 改行もちゃんと生きているでしょうか

## リンク構文

まず，行頭にある場合．

[link](https://gooogle.com)

次に，こんな風に文中に [link](https://gooogle.com) 登場するパターン．2回目 [link](https://gooogle.com) の登場にも対応できるでしょうか．

## 普通の文と改行構文

markdown は普通に文章を打つと勝手に段落になってくてるので大変便利．人にやさしいマークアップ言語です．  
行末に2つ半角スペースを入れると強制改行されます．

## 箇条書き

箇条書きには番号付きとそうでないのの2種類があります．番号がつかない箇条書きの先頭は `*`, `+`, `-` の3種類が使えます．

* 番号がないもの
	+ ネストしてても平気でしょうか
	+ 試してみましょう
		- さらにネスト
		- 試してみます
* 番号があるものもネストしてみます
	1. これがイチ
	2. これがニ
		* 普通の箇条書きに戻ってみます
		* 戻りました
* 別のものを `include` することもできます
* 例えば，[tex: \rm\TeX %] の数式やコード `\rm\TeX`
* あるいはリンク [link](https://gooogle.com) など

1. 番号があるもの
	* ネストしてても平気でしょうか
	* 試してみましょう
		* さらにネスト
		* 試してみます
2. 別のものを `include` することもできます
3. 例えば，[tex: \rm\TeX %] の数式やコード `\rm\TeX`
4. あるいはリンク [link](https://gooogle.com) など

## 表組み

これは markdown の方言です．

|SNS                 |情報                                                  |
|--------------------|------------------------------------------------------|
|Twitter             |`@` を付けたツイートは返信になります                  |
|Facebook            |[https://www.facebook.com/](https://www.facebook.com/)|

中央寄せなどを指定することも可能です．中に TeX 構文が登場するとどうなるでしょう．

|&nbsp;                    |人数       |数学好き（[tex: M=1 %]）|英語好き（[tex: E=1 %]）|
|:-------------------------|:---------:|:----------------------:|:----------------------:|
|クラス1（[tex: C_1 %]）   |30人       |5人                     |15人                    |
|クラス2（[tex: C_2 %]）   |32人       |17人                    |3人                     |

## 脚注

この形式の脚注は，はてなブログ独自
((これは私の知る限りにおいてです．))
の仕様です．必ず単独の行である必要があります．

## TeX 構文

別行立ての数式は，次のように書きます．

[tex: \int^{1}_{0}x^{3}+x^{2}+3x+e %]

複数行に渡って書くこともできます．

[tex: 
\begin{array}{l}
x^{2}+2y+1=0\\
x^{3}+5y+3=7
\end{array}
%]

文中の数式[tex: x^{2}+2x+1 %]も使えるでしょうか．

## ソースコード構文

これの実装はとても厄介でした．

```tex
\displaystyle\zeta(s)=\exp\left(\frac{\gamma+\log\pi}{2}s-\log2\right)%
\frac{1}{s-1}\prod_{\rho}\left(1-\frac{s}{\rho}\right)%
\prod^{\infty}\left(1+\frac{s}{2n}\right)e^{-{\frac{s}{2n}}}
```

1行目の言語表示がない場合や，markdown と記法がかぶる場合のソースコードはどうなるでしょうか．

```
# 概要

これは hb-converter の動作確認用の markdown ソースコードです．

* 対応しているすべての markdown 構文を内包
* 独自に採用している仕様に合致する記述

という方針のもとに作成されました．
```

この他にインラインソースコード構文 `\rm\TeX` などがあります．複数回 `puts "hoge"` 登場しても `<br>` 平気でしょうか．

インラインソースコードの中で，Markdown の記法 `[link](https://gooogle.com)` や `[tex: x^{2} %]` を使っても大丈夫でしょうか．

`\begin` インラインソースコードで始まり，インラインソースコードで終わっても対応できます．`\end`

## 画像

HTML 直打ちの画像．

<div align="center">
<img src="http://f.st-hatena.com/images/fotolife/W/WatsonDNA/20141211/20141211023313.png" width="50%">
<figcaption>画像の例：[tex: \rm\LaTeX %] 記事のアイコン</figcaption>
</div>

Markdown の構文による画像（Google Chrome アイコン）．

![Google Chrome](http://f.st-hatena.com/images/fotolife/W/WatsonDNA/20150124/20150124180252.png)

## 水平線

アスタリスクを3つ以上並べると水平線になります．

***

ハイフンやアンダースコアも使用可能です．

-------

もう一回水平線を引きます．

_____

3本の水平線が引けました．

## その他

二重の `[]` は除去されます．また，上記以外の記法（例えば，**強調**や<s>打ち消し</s>）は処理されません．

<s>これ</s>このように行頭に HTML タグが来ても対応できます．
