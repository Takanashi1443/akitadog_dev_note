# 標準的なプロジェクトの作成

## 前提

ここでは、2D、URP、ピクセルパーフェクトを使用するピクセル解像度864×480のゲームを標準とし、そのセットアップについて説明する。
必要に応じて設定は変更すること。

- 864×480は、32ピクセルを1単位とした時27×15単位に相当する。

## URP 2Dプロジェクトの作成

New Projectから2D (URP)を選択する。

### 3Dプロジェクトで作成してしまった場合

シーンビューで「2D」ボタンを押すと2Dと3Dを切り替えられる。

また、3Dと2Dではレンダラーが異なるようで、下に記載のレンダリングパイプラインの設定も必要になる。

画像ファイルのデフォルトのインポート設定が変わる。2DではSprite (UI)を選択。

### URP以外のレンダリングパイプラインで作成してしまった場合

Package Managerから「Universal RP」をインストールする。

適当な場所（プロジェクト直下など）に、Projectビューで右クリック → Create → Rendering → URP Asset(with 2D renderer)を選択して
「URPAsset」と呼ばれるものと「Renderer 2D Data」と呼ばれるものを作成する。

Project Settings → GraphicsのScriptable Rendering Pipelinesの欄に作成した「URP Asset」を入れる。

## 開発環境の設定



## シーンを新規作成

Basic(URP)を選んで新規作成する。

## ピクセルパーフェクトの設定を行う

[このページ](./../shiba_shelf/shiba_pixeler.md)を参照してピクセルパーフェクトの設定を行う。


