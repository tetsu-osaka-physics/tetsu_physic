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

5. tetsuryoku-osaka-physicsに参加する（管理者が招待送る）．（やらなくてもいい）

6. get-sty.commandをデスクトップに作る（初期設定で使ったフォルダ消した場合は入れなおす：`git clone https://github.com/tetsu-osaka-physics/setting-up.git ~/FOR
`）．ターミナル：
```
mv ~/FOR/get-sty.command Desktop/get-sty.command
cd Desktop
chmod a+x get-sty.command
```
たまに管理者がstyファイルを更新するので，時々デスクトップの`get-sty.command`を実行しましょう．

# 開発について（管理者向け）
*今後誰が開発するか知りませんが，最悪はブラウザのGitHub上でstyを編集すれば良いと思ってます．*
以下はGitを使った開発の概要（詳しい情報とかは調べれば出てくる）．

* 自分のPCにgitを入れる（上の手順）．
* リモートリポジトリを`git clone`してくる．
* `tetsu_physic`はmasterブランチとdevelopブランチ切ってる．
* ローカルブランチはdevelopだけでok．ローカルのmasterブランチは不要．
* ローカルのdevelopブランチからリモートのdevelopブランチにコミットできるよう設定．
* AtomだとgitへのコミットもGUIでできて便利．
* Atomでローカルリポジトリ（自分のmacにある`tetsu_physic`とかのフォルダのこと）を開く．
* 編集が終わったら，Atomの右下のGitてタブを開いて，左上のStage All，を押す．Commit messageに適当に入力してcommit to developを押す．
* Atom右下のGitHubタブを開いてOpen new pull requestを開く．
* ブラウザが開かれるのでプルリクを実行する．

# ブランチ関連（管理者向け）

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
