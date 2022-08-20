# ShibaShelf開発について

### 概要

ShibaShelfはゲームでよく使うコンポーネント群を機能ごとにまとめたものである。

機能ごとにまとめたものを「エレメント（Element）」と呼ぶ。

Assets直下にShibaShelfフォルダを、その中にElementsフォルダを作り、その中に各エレメントのフォルダを作る。

Elementsの名前はShibaXxxxとなるようにし、スクリプトの名前空間はShibaXxxxとする。（ShibaShelfという名前空間は作らない）

エレメントには以下のものがある。

- [ShibaPixeler](./shiba_pixeler.md) : ピクセルベースのゲームを作るためのツール。 
- ShibaTheater : いわゆる会話シーン。



### Carpenterについて

色々作ってもだいたいどう組み合わせるかなどを忘れるので、関連オブジェクト群をセットアップしやすくする仕組みとしてCarpenterというコンポーネントを各アイテムに

#### 基本的な方法

エディタ拡張する。

参考ページ:

- [Inspectorにメソッドを実行するボタンを追加する【Unity】【エディタ拡張】(2016/8)](https://kan-kikuchi.hatenablog.com/entry/CustomEditor_Button)

#### ルール

- ゲーム中は機能を発揮しない。
- 

### シーンテンプレートについて

#### 背景

Carpenterでやりたかったようなことがシーンテンプレート機能としてUnity2021で追加された。

File > Save As Scene Template で現在のシーンをシーンテンプレートとして保存できる。

参考ページ:

-[シーンテンプレートの作成](https://docs.unity3d.com/ja/2020.2/Manual/scene-templates-creating.html)

#### 基本的な方法

#### ルール


