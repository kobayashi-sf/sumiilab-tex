# docs


以下，Issuesの代わり（ただのissue用の欄なので，適切な人が独断と偏見で自由に追加・改変・削除して問題ない）

---

## ToDoや個人的所感など

- ~~（GitHubの仕様はよく知らないが，恐らく）fork先のrepoのため，issueが建てられず不便．~~
- 本repoでは，1. 卒論・修論の執筆に実質必須な最新のLaTeXテンプレートと2. 執筆時に有用なtipsの2つをメインで管理・継承すべき
    - LaTeX環境構築の話が一番重要なのかもしれない
        -  私は2018年頃からmacOSに環境構築して利用し続けていますが，長期間の利用前提なら個人的にはオススメしていません（Tex Liveのバージョンアップ時にやたらトラブる印象）
            - イマドキはHomebrew Cask経由なら大丈夫っぽい？（参考：[https://blog.wtsnjp.com/2020/07/07/about-mactex/](https://blog.wtsnjp.com/2020/07/07/about-mactex/)の注釈2）
            - [INSTALL.md](INSTALL.md)や[Linuxで文書作成：TeX の導入と利用...](https://www.youtube.com/watch?v=KXUEIgwfgL8)のようにVMのLinuxに環境構築するのが一番stableと予想
        - 変更検知の自動ビルドのためだけにOMakeとかいう標準的ではないツールを入門者に導入させるのは如何なものかと[^1] 
            [^1]:というか，バグったりもするらしい（[https://konn-san.com/prog/why-not-latexmk.html](https://konn-san.com/prog/why-not-latexmk.html)）

            - 2023年現在の自動ビルドは`latexmk -pvc`が一番standardな手法です：
                - https://tex.stackexchange.com/questions/64/tools-for-automating-document-compilation
                - https://mg.readthedocs.io/latexmk.html

            - 私はVSCodeの某拡張の機能([技術的詳細](https://github.com/James-Yu/LaTeX-Workshop/blob/dac0ee527ce0241f295ae74ebf38b89c7d1b5a41/src/components/builder.ts#L36))でやっていますが，個人的にはあまりオススメしていません（VSCodeの高機能な拡張はよくトラブルを起こすので，リテラシーがないと対処しきれないかも）
        - jlisting.styは，2023年10月現時点でmytexpertの奴はSSL認証がexpireしてリンク切れしている．CTANにもないし，再頒布されてる奴を拾うか，jvlistingで妥協するしかないかも．
          - 最近はmintedの評判がよさそうだし，どう？（[https://qiita.com/Aruneko/items/103b8419c04ad2982c14](https://qiita.com/Aruneko/items/103b8419c04ad2982c14)）
    -  研究室WiKiにも「TeXのTips」があり，tipsの記述が散乱している現状はよろしくないかも
- 卒論・修論ではあまり関係ないだろうが，基礎知識として以下ぐらいは共有されるべきかも：
    - tlmgr
    - aspell
    - bibclean
    
## その他

- 随所に現れる`https://github.com/<foo>/sumiilab-tex.git`は，引き継ぎ時に毎回最新forkのURLに置換されるべき