# tetsu_physic（教材のアレな設定）
## 内容
それぞれのstyファイルの詳しい情報は[wiki](https://github.com/tetsu-osaka-physics/tetsu_physic/wiki)を参照．
* `enumitem_extended.sty`：`enumerate`環境のラベルの種類を増やす．
* `eqnumber_extended.sty`：`align`環境での数式番号の種類を増やす．
* `Fcntr.sty`：穴埋めの四角枠を作る．
* `uw.sty`：波線を引く．

## 初回導入時の設定
ターミナル：
```sh
brew install git
mv ~/FOR/get-sty.sh ~/Desktop/get-sty.sh
chmod a+x ~/Desktop/get-sty.sh
```
**ターミナルでしたい人向け**
```sh
cp ~/Desktop/get-sty.sh /usr/local/bin/get-sty.sh
chmod a+x /usr/local/bin/get-sty.sh
```

## アップデート方法
デスクトップ上にある`get-sty.sh`を開く．パスワードの入力が必要．
たまに開発陣がstyファイルを更新するので，時々デスクトップの`get-sty.sh`を実行しましょう．
