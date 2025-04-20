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
├ External : データベースに変換するためのCSVファイルが含まれるフォルダ。
│  詳しくは[こちら](../basic_design/csv_so_database.md)を参照のこと。
│
├ (プロジェクト名)
|  ├ .gitignore : ゲームルートフォルダから見たgitignore。
   ├ Assets
      ├ (プロジェクト名)
      │  ├ Scripts : スクリプト。
      │  │  ├ Common : ゲーム全体で共通する定数クラスなど。
      │  │  ├ Special : 特別な動作をするスクリプト。
      │  │  │           
      ├

```

最も外側のフォルダ（mkdocs.ymlがあるフォルダ）をプロジェクトルートフォルダ、Unityから見たルートフォルダをゲームルートフォルダと呼ぶ。

頻出フォルダの中身へのリンク

-[Scripts/Special](#scriptsspecial)

## 補足

### フォルダ分け方針

`CommonとSpecial`

:   ゲーム全体で共通するものをCommonに入れる。例えば、ゲームのバージョンの定数など。
    ゲーム全体に影響を及ぼすものでも、それを直接参照するスクリプトが限定的なものはSpecialに入れる。
    例えば、RuntimeInitializeOnLoadMethod属性がつき、ゲーム全体の初期化を行うものはSpecialに入れる。

### 重要なフォルダの中身

#### Scripts/Special

- ThroughoutInitializer.cs: [ゲーム起動時に実行するスクリプト](./../important_function/riolm.md)
- (ProjectName)Actions.cs: [InputSystemで入力を受け取るために自動生成されるスクリプト](./../basic_design/input.md)

