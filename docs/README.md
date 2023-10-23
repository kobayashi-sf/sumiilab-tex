# docs

---

以下，Issuesの代わり（ただのissue用の欄なので，「適切な人」は独断と偏見で自由に追加・改変・削除して問題ない）


## ToDoや個人的所感など:
- ~~（GitHubの仕様はよく知らないが，恐らく）fork先のrepoのため，issueが建てられず不便．~~
- `git clone`の[https://github.com/akabe/sumiilab-tex](https://github.com/akabe/sumiilab-tex)を最新forkのURLに置換すべき
- ドキュメントは数が多いので専用ディレクトリ（ここ）に纏めるべきかも
- 本repoでは，1. 卒論・修論の執筆に実質必須な最新のLaTeXテンプレートと2. 執筆時に有用なtipsの2つをメインで管理・継承すべき
    - スライドやポスター周りの話は必須ではないので，トップのREADME.mdのトップにデカデカと乗っけておくべき話ではないかも
    -  イマドキ「EUC-JP 派の人」等の話は一般的に必要なのですか？
    -  なんなら，LaTeX環境構築の話が一番重要なのかもしれない
        -  ちなみに，私は2018年頃からmacOSに環境構築して利用し続けていますが，長期間の利用前提なら個人的にはオススメしていません（Tex Liveのバージョンアップ時にやたらトラブる印象）
            - イマドキはHomebrew Cask経由なら大丈夫っぽい？（参考：[https://blog.wtsnjp.com/2020/07/07/about-mactex/](https://blog.wtsnjp.com/2020/07/07/about-mactex/)の注釈2）
            - [INSTALL.md](INSTALL.md)や[Linuxで文書作成：TeX の導入と利用...](https://www.youtube.com/watch?v=KXUEIgwfgL8)のようにVMのLinuxに環境構築するのが一番stableと予想
        - 自動ビルドのためだけにOMakeとかいう標準的ではないツールを入門者に紹介するのは如何なものか
            - 差分検知の自動ビルドは`latexmk -pvc`がstableな中では一番standardな手法っぽいですが：
                - https://tex.stackexchange.com/questions/64/tools-for-automating-document-compilation
                - https://mg.readthedocs.io/latexmk.html
            - 私はVSCodeの某拡張の機能([技術的詳細](https://github.com/James-Yu/LaTeX-Workshop/blob/dac0ee527ce0241f295ae74ebf38b89c7d1b5a41/src/components/builder.ts#L36))でやっていますが，個人的にはあまりオススメしていません（VSCodeの高機能な拡張はよくトラブルを起こすので，リテラシーがないと大変です）
    -  研究室WiKiにも「TeXのTips」があり，tipsの記述が散乱している現状はよろしくないかも
- 卒論・修論ではあまり関係ないだろうが，基礎知識として以下ぐらいは共有されるべきかも：
    - tlmgr
    - aspell
    
