# 最初にやること

## [フォルダ構成](./folder.md)

- リンク先を読んでフォルダ構成およびMarkdown文書を作るための設定を行う。

## [Git管理](./git.md)

### 作業

- git initする。

- リンク先ページに記載されている中身で.gitignoreを作成する。
- Unityのプロジェクト設定を行う。
    - Edit > Project Settings > Editor > Asset Serialization > Mode を Force Textに
    - Edit > Project Settings > Version Control -> Mode を Visible Meta Filesに

### 参考ページ

-[UnityプロジェクトをGitで管理](https://qiita.com/cs1000/items/07368892a599b2b7b836)

## [Unity Acceleratorでの設定](../important_function/unity_accelerator.md)

- 詳細はリンク先を参照。

## 文字コード

### 作業

slnフォルダと同じ位置に「.editorconfig」ファイルを作成し、中身を以下のようにする。

```

root = true

[*.cs]
charset = utf-8-bom

```

Visual Studio Codeを最初に起動する前にやってもよい。

### 参考ページ

-[【Unity】スクリプトの文字化けに対処する](https://noracle.jp/unity_script_encode_issue/)

