# 住井・松田研究室のステキな TeX ファイルたち

[東北大学 住井・松田研究室](http://www.sf.ecei.tohoku.ac.jp/)
（工学部 電気情報物理工学科、大学院 情報科学研究科）
で使うかもしれない便利な LaTeX ファイルを公開しています。

- `paper/`: 論文のクラスファイルとサンプルファイル
- `slide/`: プレゼンテーション用の beamer サンプルファイル
- `poster/`: 学会ポスター用の beamer サンプルファイル

ちなみに、文字コードは全て UTF-8 です。[^1]
[^1]:EUC-JP 派の人は `nkf --euc` などで文字コードを変換してから使いましょう。

環境構築については [こちら](docs/INSTALL.md) を参照して下さい。

## 論文の書き方

次の一連のコマンドを実行します。

    $ git clone https://github.com/kobayashi-sf/sumiilab-tex.git
    $ cd sumiilab-tex/paper/
    $ make

きっと、カレントディレクトリには paper.pdf という論文の PDF ファイルが
出来上がっていることでしょう。
Adobe Reader (acroread) や evince で、ちゃんと表示できれば成功です。

paper.tex はクラスファイルの使用例を兼ねたテンプレートです。
これを改造すれば論文が書けます。
（論文クラスファイル自体の機能については [docs/PAPER.md](docs/PAPER.md) を参照して下さい。）

ぜひ、ステキな論文を書いて下さい。


## その他

以下の補助資料は、必要なときに読むと良いかもしれません。

- [スライドの書き方](docs/SLIDE.md):
  LaTeXでのスライドの書き方とプレゼンテーションのノウハウについて書いてあります。
- [ポスターの書き方](docs/POSTER.md):
  LaTeXでのポスターの書き方について書いてあります。
- [参考文献の書き方](docs/CITATION.md):
 スライド・論文における参考文献の書き方について書いてあります。
- [EPS 画像の作り方](docs/EPSIMAGES.md):
  LaTeX の文章に画像を入れるときは、EPS 形式を扱うことが多いです。
  普段あまり使わない画像形式なので、作り方を解説しておきます。
- [Git を使った LaTeX ファイルの管理](docs/GIT.md):
  Git を使って LaTeX ファイルを管理する方法について書いてあります。
  指導教員と論文の最新版を共有し、同時期に編集したい、という時に便利です。
  投稿論文を書くときに必要になるかもしれません。
- [フォントに関する Tips](docs/FONTS.md):
  ソースコード用のフォントの変更、日本語フォントの変更、日本語での太文字の使用、
  多書体化などのフォントに関する小技を紹介しています。
  LaTeX でフォント周りに手を加えるのは面倒なのであまりお勧めしませんが、
  デフォルトではどうしても気に入らない場合に参考にして下さい。

## 参考資料

LaTeX の文書作成に有用な（と思われる）資料です。

- [Detexify](http://detexify.kirelabs.org/classify.html):
  手書き文字から LaTeX の記号を探してくれるツールです。
  記号の出し方がわからない時は、これを使って探しましょう。
- [The Comprehensive LaTeX Symbol List (PDF)](http://www.tex.ac.uk/tex-archive/info/symbols/comprehensive/symbols-a4.pdf):
  LaTeX の記号が大量にリストアップされている PDF ファイルです。
- [日本語 LaTeX を使うときに注意するべきこと](http://www.math.tohoku.ac.jp/~kuroki/LaTeX/howtolatex.html):
  数式の体裁を整える方法について細かく書いてあって良いです。
- Beamer の使い方：
  一応、簡単な使い方は slide.tex に書いてありますが、
  詳しく知りたい人は、以下の資料に目を通してみて下さい。
  - [辻研究室 Beamer](http://neurodynamics.jp/etc/beamer):
    Beamer の機能についての説明が分かりやすくまとまっています。
    入門的な内容で、slide.tex と合わせて読むと理解が深まると思います。
  - [Beamer User Guide (PDF)](http://texdoc.net/texmf-dist/doc/latex/beamer/doc/beameruserguide.pdf):
    公式のドキュメントで、非常に詳細な情報が載っています。
- ソースコードの書き方：
  listings.sty を使いましょう（verbatim は融通が利かなくて大変不便です）。
  うまく設定すると専門書のような綺麗なソースコードが書けます。
  簡単な使い方は slide.tex に載っていますが、細かく体裁を整えたい場合は、以下の資料を読んでみて下さい。
  - [Listings - MyTeXpert](http://mytexpert.sourceforge.jp/index.php?Listings):
    `lstset` による体裁の設定の具体例が沢山載っています。
  - The Listings Package ( ftp://ftp.tex.ac.uk/tex-archive/macros/latex/contrib/listings/listings.pdf ):
    公式のドキュメントで、非常に詳細な情報が載っています。
- アルゴリズム（擬似コード）の書き方：
  algorithmic.sty と algorithm.sty を使いましょう。
  ググると比較的分かりやすい Web ページが多数ヒットします。
  - [package for algorithms](http://www.cs.toronto.edu/~frank/Useful/algorithm2e.pdf):
    公式のドキュメント。
- 証明図や導出木の書き方：
  分数を書くための frac マクロで何とかするという手もありますが、
  綺麗な証明図を書くためのスタイルファイルが幾つかあります。
  好みの問題もあるので、どれが一番良いという事はないですが、
  最初はドキュメントの多い bussproofs.sty が良いと思います（でも、bussproofs は独特のインタフェースをしています）。
  - bussproofs.sty:
    証明図や導出木則を書くためのスタイルファイルです。
    どれくらいレイアウトの融通が利くのかよくわかりませんが、
    TeX コードの見た目としては、証明図系のスタイルファイルの中で最もシンプルで分かりやすいと思います。
    - [証明図は「bussproof.sty」にお任せ](http://kreisel.fam.cx/webmaster/clog/2011-05-05-1.html):
      入門として良いと思われる Web ページ。マクロの使い方が簡潔にまとまっている。
    - [LaTeX for Logicians, bussproofs.sty: A User Guide](http://get-software.net/macros/latex/contrib/bussproofs/BussGuide2.pdf):
      公式ドキュメント。
  - proofs.sty:
    これも、証明図や導出木則を書くためのスタイルファイルです。
    - [LaTeX for Logicians, proofs.sty: A User Guide](http://www.logicmatters.net/resources/ndexamples/proofsty.html):
      簡単に使い方がまとまっています。
    - [The proof package](http://ctan.mackichan.com/macros/latex/contrib/lkproof/lkproof-doc.pdf):
      公式ドキュメント。
  - bcprules.sty:
    あの Benjamin C. Pierce 先生が作った、証明図や導出木則を書くためのスタイルファイルです。
    公式のドキュメントが見当たらないのですが、使い方は難しくないようです。
    - [推論規則をレイアウトする bcprules.sty](http://d.hatena.ne.jp/eagletmt/20120111/1326251578):
      bcprules.sty の具体例が載っています。

---
Issuesの代わり：[docs/README.md](docs/README.md)
