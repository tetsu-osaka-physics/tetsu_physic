# tetsu_physic（教材のアレな設定）
## 内容
* circle_eqnumber.sty：align環境での数式番号を丸数字にする．参照はeqrefを使うと，丸数字になる．
* enumitem_extended.sty：enumerate環境の番号を更に増やしたもの．カウンターの出力型としても使える．
* Fcntr.sty：穴埋め形式の問題で，数字を自動更新する．表示の仕方は，enumitem_extendedとほぼ同じ（アスタリスクがつかない）．
* uw.sty：最低1emは波線を出力する．オプションで`_{\f{}}`を自動出力する．
* h XXX.sty：高２，高３の教材など．目的に合わせて使い分ける．
## ユーザー権限について
GitHubのアカウントを作ってもらいますが，今のところ，各ユーザーはreadonlyにしようと考えています．
もし，「自分も編集に参加したい！」という場合は，気軽に言ってください．
## アップデート方法
デスクトップ上にある`get-sty.command`を開けば，
1. 既存の`/usr/local/texlie/texmf-local/tex/latex/tetsu_physic`を削除する
2. `git clone`で`/usr/local/texlie/texmf-local/tex/latex/tetsu_physic`にリポジトリを移植
3. `/usr/local/texlive/local/texlive/texmf-local/tex/latex/tetsu_physics/.git`を削除（リポジトリ化を解除）
4. ls-Rファイル作成の実行（TeXが見つけられるようにするための設定）

を自動で行います．パスワードの入力が必要です．
## 初回導入時の設定
1. GitHubアカウントの設定（やらなくてもいい）
2. gitの導入
```
brew install git
```
3. gitアカウントの設定（やらなくてもいい）
```
git config --global user.name="<username>"
git config --global user.email=<address@mail.com>
```
4. 鍵の生成（やらなくてもいい）
```
mkdir ~/.ssh
cd ~/.ssh
ssh-keygen -t rsa
atom id_rsa.pub
```
で公開鍵をコピペして，自分のGitHubのページで鍵を入れて認証する．

5. tetsuryoku-osaka-physicsに参加する（招待送ります）．（やらなくてもいい）

6. get-sty.commandを実行します（初期設定で使ったフォルダ消した場合は入れなおす）．ターミナル：
```
mv ~/FOR/get-sty.command Desktop/get-sty.command
cd Desktop
chmod a+x get-sty.command
```
を実行します．

## ブランチ関係（特にリモート）
* リモートのブランチ削除
```
git push --delete origin [branch name]
```
* リモートで既に消えているが，ローカルには参照が残っている場合
remoteブランチを単純参照して，remoteブランチでは削除されているがローカルに参照が残っているブランチを表示して，すでに削除されているremoteブランチのローカル参照を削除してきれいにする
```
git remote show origin
git remote prune --dry-run origin
git remote prune origin
```
複数のPCで作業する場合，ローカルのdevelopブランチでの`git push`で`origin/master`に通ってしまうことがあるので注意（バグが残ったものを`origin/master`に上げると顰蹙を買う）．`git push`でのpush先のリモートブランチを変更する時は，
```
git branch [local branch name] --set-upstream-to origin/[remote branch name]
```
