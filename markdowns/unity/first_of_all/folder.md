# Unityのフォルダ構成

## フォルダ構成

### 構成

```
.
├ mkdocs.yml
├ .gitignore : Gitで管理しないフォルダ・ファイルを記載。
│
├ markdowns : MarkDownファイル群が入っている。通常はdocsという名前のフォルダだが、設定で変更している。
├ docs : buildコマンドでHTMLファイル群が格納される。
├ materials : 作図用PowerPointファイルなど、直接Webサイトとして公開しないが、共有するファイル群。
├ raw_materials : 個人情報が含まれるスクリーンショットなど。Git管理しない。
│  これらのフォルダの運用方法はこのドキュメントと同じ。
|
├ (プロジェクト名)
|  ├ .gitignore : ゲームルートフォルダから見たgitignore。
   ├ Assets
      ├ (プロジェクト名)
      │  ├ Common : ゲーム全体で共通する定数など。
      │  ├ Special : 特別な動作をするもの。
      ├

```

最も外側のフォルダ（mkdocs.ymlがあるフォルダ）をプロジェクトルートフォルダ、Unityから見たルートフォルダをゲームルートフォルダと呼ぶ。

### 補足

`CommonとSpecial`

:   ゲーム全体で共通するものをCommonに入れる。例えば、ゲームのバージョンの定数など。
    ゲーム全体に影響を及ぼすものでも、それを直接参照するスクリプトが限定的なものはSpecialに入れる。
    例えば、RuntimeInitializeOnLoadMethod属性がつき、ゲーム全体の初期化を行うものはSpecialに入れる。

## mkdocsの操作

プロジェクトルートフォルダ内で

```

mkdocs new .

```

とすると、プロジェクトルートフォルダをmkdocsのプロジェクトフォルダとし、docsフォルダとmkdocs.ymlが作成される。

以下の処理を行う。

- mkdocs.ymlの中身を、例として以下のようにする。

```

site_name: My Docs
docs_dir: markdowns
site_dir: docs
theme:
  name: material
markdown_extensions:
  - def_list
nav:
  - Home: 'index.md'

```

- 「docs」フォルダを「markdowns」に変更。

- mkdocs serveをコマンドラインから実行し、ローカルサーバが起動してWEBページを開けることを確認。
- 複数のドキュメントを同時に開く場合、このようなコマンドにより複数ページをserveすることができる。

```

mkdocs serve --dev-addr=127.0.0.2:8000

```


# 参考ページ

-[MkDocsの使い方](https://zenn.dev/shotakaha/scraps/1aab3983e63624)
-[Material for MkDocsで生成したサイトをGithub Pagesで公開する](https://zenn.dev/y16ra/articles/6266a87b048bd2)

