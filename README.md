# 住井研究室のステキな TeX ファイルたち

東北大学 情報科学研究科 住井研究室で使う（かもしれない）便利な LaTeX ファイルを公開しています。

- `paper/` : 論文のクラスファイルとサンプルファイル
- `slide/` : プレゼンテーション用の beamer サンプルファイル

ちなみに，文字コードは全て UTF-8 です．
EUC-JP 派の人は `nkf --euc` などで文字コードを変換してから使いましょう．

## LaTeX 環境の構築

### Linux 環境の構築（最低限）

#### Linux のインストール

まずは，Linux を VMware などでインストールしましょう．
インストーラの指示に従って「はい」と答えるだけの簡単なお仕事です．
今回は Debian をインストールしたことにしましょう．
（Ubuntu などでも構いません．）

#### 基礎知識：スーパーユーザ（root ユーザ）

このあとのインストール手順ではコンソールにコマンドを入力して実行する操作が登場しますが，
プロンプトの記号で一般ユーザでの実行なのか，スーパーユーザでの実行なのかを区別します．
（コンソールに表示されている `sumiilab@pubpc:~/foo/$` を _プロンプト_ と言います．
コマンドの説明をするときは，省略して `$` のように書くことが多いです．）

- `$` は一般ユーザでの実行（例: `$ ls` は一般ユーザで `ls` を実行）
- `#` はスーパーユーザでの実行（例: `# ls` はスーパーユーザで `ls` を実行）

`$` や `#` 自体はコマンドではないので，入力しません．
一般ユーザからスーパーユーザに切り替えるときは，一般に `su` コマンドを使います．

    $ su
    Password:
    #

ちなみに，パスワードは入力しても画面に表示されないので注意して下さい．
Ubuntu では `su` コマンドの代わりに，`sudo` コマンドを使います．
`sudo` は特定のコマンドだけをスーパーユーザとして実行するためのもので，

    $ sudo ls

のように，一般ユーザで `sudo` の後に実行したいコマンドを書きます．
Ubuntu を使っている人は `#` を `$ sudo` に適宜置き換えて実行して下さい．

#### パッケージの追加

Debian では，よく使うソフトウェアなどをパッケージという単位でサーバに保存し，管理しています．
そして，コマンドを叩くだけで，それらのパッケージをインストールする仕組みがあります．
デフォルトの設定だと，インストールできるパッケージが限られていて不便なので，増やしておきましょう．

パッケージをダウンロードするためのサーバ情報は `/etc/apt/sources.list` という設定ファイルに
書かれています．これを少し書き換えてみます．

まずは，念の為にバックアップを作っておきます．

    # cd /etc/apt
    # cp sources.list sources.list.bak

スーパーユーザで設定ファイルをいじるときは，バックアップを取るのが常識です．
設定ミスで変な動作をするときは `mv sources.list.bak sources.list` で以前の状態に戻せます．

次に，この設定ファイルの各行の行末に `contrib non-free` というキーワードを追加します．
これで，インストールできるパッケージが増えます．
いちいち，エディタで書き換えてもいいですが，次の2つのコマンドを実行しても同じ事ができます．

    # perl -i -ple '$_ .= " contrib" if /deb/ && !/contrib/' sources.list
    # perl -i -ple '$_ .= " non-free" if /deb/ && !/non-free/' sources.list

そして，最後にサーバからパッケージのリストをダウンロードしてきます．

    # aptitude update

Ubuntu を使っている人は上のコマンドの代わりに `sudo apt-get update` を使います．
ちなみに，`aptitude` や `apt-get` は CUI のパッケージ管理ソフトです．
Debian だと両方のコマンドが使えますが，`aptitude` は `apt-get` のフロントエンドなので，
`aptitude` の方をオススメします．

### TeXLive とその他必要なソフトウェアのインストール

次のコマンドで TeXLive とその他必要なソフトウェアをインストールできます．

    # aptitude install texlive-full texlive-lang-cjk git imagemagick inkscape gimp

### スタイルファイルのインストール

スタイルファイルというのは，便利なマクロなどをまとめた TeX ファイルのことです．
基本的にスタイルファイルは，コンパイルする TeX ファイルと同じディレクトリに置けば読み込まれますが，
新しく論文やスライドを作る度にスタイルファイルをコピーするのは面倒なので，
よく使いそうなものはインストールすると良いです．

住井研究室で，よく使いそうなスタイルファイルについては自動でまとめてインストールするためのインストーラを用意しました．

    $ git clone https://github.com/akabe/sumiilab-tex
    $ cd sumiilab-tex
    # ./install.sh

上のコマンドを実行すると，勝手にスタイルファイルをダウンロードしてきて，インストールしてくれます．
どのようなスタイルファイルがインストールされるかについては，`install.sh` を参照して下さい．

sumiilab-tex リポジトリは時々アップデートされるかもしれません．
そのときは，上記のコマンドを再度実行することで，スタイルファイルの追加や更新が行えます．
（時々，この手順でスタイルファイルの追加・更新を行うことをオススメします．）

### 環境構築が終わったら

苦労の末に完成した LaTeX 環境を早速使ってみましょう．
試しに，スライドでもコンパイルしてみましょう．

## スタイルファイルの使い方

### スライドの書き方

まず，次の一連のコマンドを実行して，`slide.pdf` が作れるか確認しましょう．

    $ git clone https://github.com/akabe/sumiilab-tex
    $ cd sumiilab-tex/slide/
    $ make

きっと，カレントディレクトリには slide.pdf というスライドの PDF ファイルが
出来上がっていることでしょう．

    $ ls
    Makefile slide.pdf ...

PDF ファイルをちゃんと表示できれば成功です．

    $ evince slide.pdf &

evince は Debian に標準でインストールされているドキュメント・ビューアで，
tex ファイルを再コンパイルしたときに，勝手にリロードして，表示を更新してくれるので便利です．
もしも，日本語が文字化けしたりして，うまく表示できないときは，純正の Adobe Reader を使いましょう．

    $ acroread slide.pdf &

もし，純正の Adobe Reader でも文字化けするようなら，フォントの設定がおかしいか，
うまくインストールできなかった可能性があります．ググるか，詳しい人に聞いて直しましょう．
（Adobe Reader は Adobe の公式 Web ページからダウンロードしてきた，.bin ファイルに
`chmod a+x ***.bin` でパーミッションを与えた後，`./***.bin` でインストールできます．）

slide.tex を改造すれば，スライドが作れます．
コンパイルは `make` でできます．

※ 論文とは違って，スライドに関しては特定のフォーマットが決められているわけではありません．
好きに改造してもらって結構です．
（Power Point で作っても構いませんし，自信があるなら，スライドを使わずに，板書だけで説明しても OK です．）

以下は良いスライド，良い発表のコツです．
あくまで，学生が勝手にまとめただけの内容なので，あまり参考にならないかもしれません．

- 発表するとき，発表者であるあなたは内容について熟知していますが，聞いている人にとっては初見の内容かもしれません．
  専門用語はちゃんと説明しましょう．難しい用語や概念は直感的理解や具体例を述べた後に，
  形式的な定義を話すと理解されやすいです．
- スライドを作るときは，そのページで「何を説明したいか？」「どんなことを伝えたいか？」といった，
  説明の目的・目標を意識すると良いです．
  関係のない複数の内容を1つのページにまとめて書いたりすると，聞いてる人は混乱してしまいます．
- 関係のない項目や種類の違う項目のようなを1つの箇条書きの中に収めたり，意味もなく矢印を使ったりするのも，
  聞き手を混乱させる原因になります．
- 他人の論文を読んで，その内容について発表するときは，論文と全く同じ順序で説明をする必要はありません．
  むしろ，解りやすくなるように，説明の順序を入れ替えたほうが，より良い発表になります．
  普通，論文では論理の筋道が通るように，記号や関数，定理や補題は使う前に定義をしています．
  しかし，口頭発表において同じ順序で説明すると，聞いている人は「その関数何に使うの？」といった疑問を持つことが多いです．
  また，議論の大筋と関係のない記号等の定義が続くと，聞いている人は話の流れを見失ってしまいます．
  発表するときは，議論の筋道が聴衆に伝わるように説明すると良いです．
  （例えば，議論の大筋と重要な関係がないような記号の定義などは，必要になったら説明する，など．）
- アイディアなどを説明するための具体例は，無闇に複雑なものだと，聴衆に内容が伝わらない可能性があります．
  説明したい項目や概念を予め考えて（列挙して）おいて，それを最小限に含むような具体例を作ると良いです．
- 幾つかの項目や概念を順番に説明したい時には，必要な情報を一気に見せるのではなく，
  必要になった時に表示するほうが効果的です．最初から，全ての情報を見せると，
  発表者が「今現在説明している内容」の理解に必要な情報と，
  「これから（未来に）話す内容」の理解に必要な情報が混在してしまい，
  聴衆はどこに注目して話を聞けば良いかわからなくなります．
  アニメーション等を使ったり，スライドを分けるなどして，未来に必要になる情報を隠しておくと良いです．
  （ただし，アニメーションといっても，非常に簡素なものに留めたほうが良いです．）

### 論文の書き方

次の一連のコマンドを実行します．

    $ git clone https://github.com/akabe/sumiilab-tex
    $ cd sumiilab-tex/paper/
    $ make

きっと，カレントディレクトリには paper.pdf という論文の PDF ファイルが
出来上がっていることでしょう．
Adobe Reader (acroread) や evince で，ちゃんと表示できれば成功です．

paper.tex はクラスファイルの使用例を兼ねたテンプレートです．
これを改造すれば論文が書けます．
（論文クラスファイル自体の機能については [PAPER.md](PAPER.md) を参照して下さい．）

#### BibTeX

BibTeX は LaTeX で参考文献を管理するためのツールです．
使わなくても，参考文献を書くことは可能ですが，自力で体裁を整えるのは結構大変なので，
BibTeX を使って，自動で参考文献の一覧を生成したほうが楽です．
paper.tex も標準で BibTeX を使うようになっています．

参考文献は refs.bib に追加しましょう．
「文献の著者(or 題名) + DBLP + bibtex」でググると，大抵は BibTeX の書き方が出てくるので，
それを流用するといいでしょう．

##### URL を参考文献に載せる

論文になっていないライブラリを参考文献にしたいときなどは，自力で URL を参考文献に追加する必要があります．
このときは，

    @misc{ID,
    author={著者の名前},
    title={タイトル},
    howpublished={\url{http://...}},
    year={20XX}}

のようなエントリを，resf.bib に追加します．
`ID` は paper.tex から参照するときの名前（識別子）で，参照するときは `\cite{ID}` のようにします．
例えば，

    @misc{JaneStreetCore,
    author={Jane Street},
    title={{J}ane {S}treet {C}ore},
    howpublished={\url{http://janestreet.github.io/}},
    year={2014}}

とかね．（`{...}` で囲むと大文字になります．）

##### DBLP に関する注意

DBLP の BibTeX データは比較的信頼できますが，ときどき間違っています．
特に，固有名詞の中で大文字になるべき文字が小文字になっていることが多いです
（例えば，OCaml が ocaml になっていたり，GADT が gadt になっていたりなど）．
BibTeX は文献題目などの先頭以外の文字を勝手に小文字に変換するので，
大文字にしたいところを明示的に `{...}` で囲む必要があることに，注意して下さい．
例えば，

    @article{...,
    author = {John Smith},
    title  = {Functional programming in OCaml},
    ...}

と書いてあった場合，参考文献のタイトルが "Functional programming in ocaml" になってしまうので，

    @article{...,
    author = {John Smith},
    title  = {Functional programming in {OC}aml},
    ...}

と書き直します．

ぜひ，ステキな論文を書いて下さい．

## EPS 画像の作り方

LaTeX の文章に画像を入れるときは，EPS 形式を扱うことが多いです．
例えば，`\includegraphics{foo.eps}` のようにして，画像を文章中に埋め込みます．
ここでは，EPS を作る方法を幾つか紹介します．

### JPEG 等の画像を EPS に変換する方法

既に手元にある JPEG，GIF，PNG 等の画像をそのまま EPS 画像に変換するには ImageMagick の
convert コマンドを使うと良いです．
例えば，`baz.jpg` を `foo.eps` に変換したい場合は，

    $ convert baz.jpg foo.eps

とします．
convert コマンドは画像の加工も行えますが，画像編集に関しては GIMP の方が扱いやすいです．

### JPEG 等の画像を編集して EPS に変換する方法

画像の編集が必要なときは GIMP を使うと良いでしょう．
コンソールで `$ gimp &` としても良いですし，アプリケーションのメニューから立ちあげても構いません．
使い方については各自調べて下さい．

### イラストを作る場合

ベクタ形式の画像を作る場合は Inkscape が良いです．
これも，コンソールで `$ inkscape &` としても良いですし，アプリケーションのメニューから立ちあげても構いません．
使い方については各自調べて下さい．

## Git で TeX ファイルを管理する

研究の過程で，論文や証明の内容などを TeX で作って，先生と共有したいことはよくあります．
オンラインストレージを使っても良いですが，Git を使うと便利です．Git で管理すると，変更の履歴が残る他，
同じファイルに違う変更を「同時に」行った場合に，変更をマージする，といった作業をある程度自動的にやってくれます
（手動で行う必要がある部分もありますが，適切に操作すれば，ファイルが破損することは避けられます）．
ここでは，TeX で論文などの TeX ファイルを管理する方法について，ごく簡単に解説します
（Git は複雑で，詳細な解説をここに書くのは不可能なので，他の文献などとあわせて読むと良いです）．

Git 用語の（雑な）解説:

- リポジトリ：ソースコードの変更履歴の情報を集めたデータ・ベース
- リモート・リポジトリ：サーバー上にあるリポジトリで（アクセス権があれば）誰でもアクセスできる
  - プライベート・リポジトリ：登録した人以外はアクセスできない非公開なリポジトリ
  - パブリック・リポジトリ：誰でもアクセスできる公開されたリポジトリ
  - push：ローカル・リポジトリの内容をリモート・リポジトリに反映（アップロード）すること (`git push`)
- ローカル・リポジトリ：ローカル（あなたのパソコンの中）にあるリポジトリ（当たり前だが，外からクセスできない）
  - commit：ローカル・リポジトリにファイルの変更を記録すること (`git commit`)
  - stage：これからコミットするファイルを指定すること (`git add`)

### 1. アカウントを作る

まずは，GitHub か Bitbucket にアカウントを作ります（どちらで作るべきかは，先生に相談して下さい）．
一応，大雑把な比較を載せておきます．がっつり使う気がなければ，どちらも大差ありませんが，
プライベート・リポジトリの数量と共有人数の上限についてだけ気にすると良いと思います．
パブリック・リポジトリの数量は GitHub も Bitbucket も無制限です．

- [GitHub](https://github.com/): 全般的に機能が豊富で使いやすいが，
  プライベート・リポジトリが有料です．
  学生である場合は，https://education.github.com/ から申請することで，
  2年間だけ有料の Micro プラン（$7/月，プライベート・リポジトリは5つまで，共有人数は無制限）を無料で使うことができます．
  申請の際に，大学のメールアドレスと申請理由を書く必要があります．
  申請理由は「大学生です．研究のためにプライベート・リポジトリを使いたい．」みたいなことを英語で2〜3行書くだけです．
- [Bitbucket](https://bitbucket.org/): Git と Mercurial が使える．
  プライベート・リポジトリは無料で数量無制限であるが，全てのプライベート・リポジトリの共有人数の合計は5人が上限です．
  共有人数を増やすのには，お金がかかります．

### 2. Git の初期設定

次のコマンドで，あなたの名前・メルアド・エディタを設定します（エディタは vi でも何でも可）．

    $ git config --global user.name "Taro Yamada"                   # あなたの名前
    $ git config --global user.email "yamada@sf.ecei.tohoku.ac.jp"  # あなたのメルアド
    $ git config --global core.editor emacs                         # エディタは emacs

Git の表示に色つけして欲しい時は，次のコマンドで設定できます．

    $ git config --global color.ui auto        # git の表示に色つけする
    $ git config --global core.pager 'less -R' # pager は less -R

色つけして，表示がおかしくなる時は，次のコマンドで無効化できます．

    $ git config --global color.ui false    # git の表示に色つけしない
    $ git config --global core.pager 'less' # pager は less

いちいち，Enter でスクロールするのがうざい時は pager に空文字列を設定します．
この場合，出力文字列がどんなに長くても，一気にドバっと出力されます．

    $ git config --global core.pager '' # pager を使わない

### 3. ローカル・リポジトリの作成（初期化とコミット）

まずは，Git のローカル・リポジトリを初期化します．

    $ cd sumiilab-tex/slide  # 論文の場合は sumiilab-tex/paper
    $ git init  # ディレクトリを Git リポジトリとして初期化
    Initialized empty Git repository in /home/***/sumiilab-tex/slide/.git/

これで，空のローカル・リポジトリができました．
次に，ローカル・リポジトリにファイルをコミットします．

    $ make clean  # 不要なファイルを予め削除しておく
    $ cp ../.gitignore .
    $ echo "# 私のステキな TeX ファイルたち" > README.md
    $ git add .  # コミットする予定のファイルを index に登録（stage すると言います）
    $ git commit -m "first commit"  # コミットする
    [master (root-commit) 4ba8943] first commit
    5 files changed, 521 insertions(+)
    create mode 100644 .gitignore
    create mode 100644 Makefile
    create mode 100644 README.md
    create mode 100644 beamerthemesumiilab.sty
    create mode 100644 slide.pdf
    create mode 100644 slide.tex

`git commit -m "..."` の `...` の部分に「コミット・メッセージ」つまり「変更の内容」を簡潔に記載します．
長いメッセージを書きたい時は，`git commit` だけ打つと，エディタが起動するので，1行目に変更の内容を簡潔に記載し，
2行目を空行にして，3行目以降に詳細なメッセージを書きます．その後，ファイルを（上書き）保存して，エディタを終了すると，
コミットされます．コミットのログは `git log` で表示できます．

    $ git log
    commit 4ba8943ab2f20c0ae8b843a8d022592187d59da0
    Author: Taro Yamada <yamada@kb.ecei.tohoku.ac.jp>
    Date:   Tue Sep 23 12:29:21 2014 +0900

    first commit

### 4. リモート・リポジトリの作成

GitHub もしくは Bitbucket 上で，リポジトリを作ります（Bitbucket の場合はバージョン管理に Git を選択）．
その際に，パブリック（公開）にするかプライベート（非公開）にするか選び，
空のリポジトリを作成します（README.md，.gitignore や LICENSE ファイルを作成しないこと）．
そして，ローカル・リポジトリに，リモート・リポジトリのアドレスと名前（ここでは origin）を登録しましょう．

    $ git remote add origin https://[username]@github.com/[username]/[repository]

`[username]`，`[repository]` に，それぞれあなたのアカウント名とリポジトリ名を入れます．
例えば，`yamada` というアカウントで，`test42` という名前のリモート・リポジトリを作ったときは，
`git remote add origin https://yamada@github.com/yamada/test42` になります．
このあと，

    $ git push -u origin master

とすると，いままで登録したコミットをリモート・リポジトリにアップロードします．

### 5. Collaborators の登録

プライベート・リポジトリについて，無関係な人には内容を公開せず，
特定の人（例えば，先生）にだけ内容を見えるようにしたい時は，
リポジトリの Collaborators に「特定の人」のアカウントを追加します．
GitHub では，右メニューの "Settings" → "Collaborators" から登録できます．
Bitbucket では，やったこと無いけど，簡単にできるんじゃないでしょうか？

### 6. その後の使い方

あとは，基本的に

1. 新しくファイル（画像とか）を追加したら `git add [filename]` で stage する
2. ファイルの変更したら `git commit -a` もしくは `git commit -a -m "..."` でローカル・リポジトリに登録
3. アップロードするときは `git push`

の流れを繰り返すだけです．ただし，`git push` したときに「マージできない」みたいなエラーが出た場合は
自分以外の collaborator(s) が別な変更をファイルに加えている可能性があるので，

    $ git pull

でリモート・リポジトリの最新の内容をローカル・リポジトリに取り込みます．
そのあと，マージに失敗した箇所を手動で編集していきます．（手動マージについては，ググってください．）

## 参考資料

LaTeX の文書作成に有用な（と思われる）資料です．

- [The Comprehensive LaTeX Symbol List (PDF)](http://www.tex.ac.uk/tex-archive/info/symbols/comprehensive/symbols-a4.pdf):
  LaTeX の記号が大量にリストアップされているので，必要な記号を探すのに良いです．
  PDF なので，ダウンロードしてすぐに参照できるようにしておくと良いでしょう．
- [日本語 LaTeX を使うときに注意するべきこと](http://www.math.tohoku.ac.jp/~kuroki/LaTeX/howtolatex.html):
  数式の体裁を整える方法について細かく書いてあって良いです．
- Beamer の使い方：一応，簡単な使い方は slide.tex に書いてありますが，
  詳しく知りたい人は，以下の資料に目を通してみて下さい．
  - [辻研究室 Beamer](http://neurodynamics.jp/etc/beamer):
    Beamer の機能についての説明が分かりやすくまとまっています．
    入門的な内容で，slide.tex と合わせて読むと理解が深まると思います．
  - [Beamer User Guide (PDF)](http://texdoc.net/texmf-dist/doc/latex/beamer/doc/beameruserguide.pdf):
    公式のドキュメントで，非常に詳細な情報が載っています．
- ソースコードの書き方：listings.sty を使いましょう（verbatim は融通が利かなくて大変不便です）．
  うまく設定すると専門書のような綺麗なソースコードが書けます．
  簡単な使い方は slide.tex に載っていますが，細かく体裁を整えたい場合は，以下の資料を読んでみて下さい．
  listings.sty は slide.tex でも paper.tex でもデフォルトで読み込まれるので，
  自分で `usepackage` する必要はありません．
  - [Listings - MyTeXpert](http://mytexpert.sourceforge.jp/index.php?Listings):
    `lstset` による体裁の設定の具体例が沢山載っています．
  - The Listings Package ( ftp://ftp.tex.ac.uk/tex-archive/macros/latex/contrib/listings/listings.pdf ):
    公式のドキュメントで，非常に詳細な情報が載っています．
- アルゴリズム（擬似コード）の書き方：algorithmic.sty と algorithm.sty を使いましょう．
  ググると比較的分かりやすい Web ページが多数ヒットします．
  - [package for algorithms](http://www.cs.toronto.edu/~frank/Useful/algorithm2e.pdf):
    公式のドキュメント．
- 証明図や導出木の書き方：分数を書くための frac マクロで何とかするという手もありますが，
  綺麗な証明図を書くためのスタイルファイルが幾つかあります．
  好みの問題もあるので，どれが一番良いという事はないですが，
  最初はドキュメントの多い bussproofs.sty が良いと思います（でも，bussproofs は独特のインタフェースをしています）．
  - bussproofs.sty:
    証明図や導出木則を書くためのスタイルファイルです．
    どれくらいレイアウトの融通が利くのかよくわかりませんが，
    TeX コードの見た目としては，証明図系のスタイルファイルの中で最もシンプルで分かりやすいと思います．
    - [証明図は「bussproof.sty」にお任せ](http://kreisel.fam.cx/webmaster/clog/2011-05-05-1.html):
      入門として良いと思われる Web ページ．マクロの使い方が簡潔にまとまっている．
    - [LaTeX for Logicians, bussproofs.sty: A User Guide](http://get-software.net/macros/latex/contrib/bussproofs/BussGuide2.pdf):
      公式ドキュメント．
  - proofs.sty:
    これも，証明図や導出木則を書くためのスタイルファイルです．
    - [LaTeX for Logicians, proofs.sty: A User Guide](http://www.logicmatters.net/resources/ndexamples/proofsty.html):
      簡単に使い方がまとまっています．
    - [The proof package](http://ctan.mackichan.com/macros/latex/contrib/lkproof/lkproof-doc.pdf):
      公式ドキュメント．
  - bcprules.sty:
    あの Benjamin C. Pierce 先生が作った，証明図や導出木則を書くためのスタイルファイルです．
    公式のドキュメントが見当たらないのですが，使い方は難しくないようです．
    - [推論規則をレイアウトする bcprules.sty](http://d.hatena.ne.jp/eagletmt/20120111/1326251578):
      bcprules.sty の具体例が載っています．
