# MkDocs

## 基本事項

`ローカルサーバ起動`

:   MkDocsフォルダでコマンドプロンプトを起動、mkdocs serve

`HTMLファイル群をビルド`

:   MkDocsフォルダでコマンドプロンプトを起動、mkdocs build。
    出力先フォルダを変えることもできる。

```
mkdocs build -d XXXX
```

`色々設定`

:   ルートフォルダのmkdocs.ymlをいじる

## 参考サイト

- [MkDocsを使って、簡単にドキュメント公開♪](https://qiita.com/yagizo/items/fef66728f97b866a3bee)

## Markdown記法

`定義リスト`

:   定義したい語をバッククォーテーションで囲み、定義をコロン＋タブの後に入力。
    前もってmkdocs.ymlに下記を追加する必要あり。

```
markdown_extensions:
  - def_list
```

## その他

`Markdownファイル群を入れるフォルダを変更する`

:   mkdocs.ymlに追記。例えばmarkdownsフォルダに入れるには

```
docs_dir: markdowns
```

`ナビゲーションバー`

: [このページ](https://mkdocs.nakaken88.com/use/write/)を参考に、mkdocs.ymlのnavセクションに記載。