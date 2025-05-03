# TextMeshPro

## 導入

- Package Managerからインストール。（最初から入っていることも）
- 最初に「Window」→「TextMeshPro」→「Import TMP Essential Resources」で最低限使用するリソースをインストールする必要がある。
- 使用する文字のファイルを準備。文字コードはUTF-8Nで。
- 「Create」→「TextMeshPro」→「Font Asset」でフォントをメッシュ化したアセットを作成。フォントと使用する文字ファイルを指定する。
- 「UI」→「Text」→「TextMeshPro」でCanvas上にテキストを描画。

## 引っかかった点

文字を選んで登録する場合、アンダーバーの文字を使用していなくても、「アンダーバーの文字がありません」という警告が出る場合がある。

使用する文字ファイルにアンダーバーと両括弧（半角）を追加すると出なくなる。

# めんどくさいから日本語の文字を一通り登録する

[このページ](https://www.midnightunity.net/textmeshpro-japanese-font/)などを参照。

## 参考ページ

- [UnityのTextMeshProを使ってみる](https://gametukurikata.com/ui/textmeshpro)
- [TextMesh Pro で日本語フォントを使う方法【Unity】](https://www.midnightunity.net/textmeshpro-japanese-font/)
