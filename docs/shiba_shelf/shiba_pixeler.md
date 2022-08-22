# ShibaPixeler

## はじめに

ShibaPixelerはピクセルベースの2Dゲームのベース部分を作るためのツールである。

Unityは基本的にピクセルベースを考慮していないが、ピクセルベースのゲーム制作に慣れているし、ピクセルベースのゲームの想像の余地がある感じは魅力的である。

Unityに追加されたピクセルパーフェクトカメラというコンポーネントを使うためのスクリプトなどで構成される。

## 最初に決めること

- Unity上の1単位（1m）あたりのピクセル数(PPU) : 16, 32など
- 画素数（ウィンドウサイズとは異なる）: 標準では864x480（PPUが32の時、27×15単位）
- 標準的なウィンドウサイズ（通常、画素数の整数倍）: 標準では1732x960 (画素数の2倍)

## PixelerUnitで定義される定数

PixelerUnitクラスで、ゲームで共通して使用する定数を定義する。

- PPU : ピクセルパーユニット。Unity上の1mに何ピクセルが入るか。
- CellWidth : ゲームにおいて「セル」の概念を使用する際の横幅。
- CellHeight : セルの縦幅。

## プロジェクト設定

2Dのプロジェクトであることが前提。

### Pixel Perfect Cameraを使用できるようにする

Package Managerで、Unityのレジストリ内から「2D Pixel Perfect」をインストールする。

新しいUnityバージョンであれば2Dプロジェクトには標準でインストールされている。

## 素材設定

スプライトのインポート時、以下の設定を行う。

- Sprite ModeのPixels Per Unitを最初に決めた数値(16, 32など)に
- AdvancedのFilter Modeを「Point (no filter)」に
- CompressionをNoneに : None以外だと画像が圧縮されてしまう場合がある

## カメラ設定

### Pixel Perfect Cameraのアタッチ

シーンで使用するMainCameraに「Pixel Perfect Camera」コンポーネントをアタッチする。

URP用とBuilt-In用に同名のコンポーネントが存在する。現在のパイプラインでない方を選ぶとWarningが出るので、出たら違うのを選ぶ。

プロジェクト作成時に3Dで作成していると、2D用のレンダリングパイプラインが必要ですといったエラーが出る。

[このページ](./../unity_rules/create_standard_project.md)を参考にレンダリングパイプラインアセットを新規作成し、設定する。

### コンポーネントの設定

Pixel Perfect Cameraコンポーネントで以下の設定を行う。

- Assets Pixels Per Unitを最初に決めた数値(16, 32など)に
- Reference Resolutionを画素数(864x480)に
- Grid Snappingを「Pixel Snapping」に
    - この設定にしないと画面を整数倍以外で拡大した際にピクセル間がいびつになる場合があるらしい。
- Crop Frameを「Stretch Fill」にすると、指定した比率を保ったまま画面サイズに合わせて拡大し、はみ出た分は黒塗りにしてくれる
    - iPhoneアプリだと左上の画素が黒いのは良くないらしい？（詳細不明）
    - 標準では使用するが、制約上多少はみ出ても大丈夫なゲームならNoneの方が見た目が良さそう。

## UI用の設定

UI描画用のCanvasコンポーネントを追加する際、それぞれに以下の設定を行う。

- Render Modeを「Screen Space - Camera」にする。
- Canvas Scalerの「UI Scale Mode」を「Scale With Screen Size」にする。
- Reference Resolutionを画素数と同じにする。
- 「Reference Pixels Per Unit」を最初に決めた数値にする。

- ピクセルパーフェクトカメラ側でピクセルパーフェクトするので、Canvas側ではPixel Perfectはチェックしなくても良さそう。（負荷が大きいらしい）→ 今後要検討

## ゲームビューの設定

想定するゲームのウィンドウサイズを設定する。

## 参考ページ

- [【Unity】Pixel Perfect Cameraでレトロな画面を再現する【2D Pixel Perfect】](https://gamedev65535.com/entry/unity_pixelperfetccamera/)
- [【Unity】Pixel Perfect（ピクセル・パーフェクト)にする方法](https://kazupon.org/unity-pixel-perfect-settings/)
- [Snap to Grid with Pixel Perfect Camera - Point & Click Unity Tutorial](https://www.youtube.com/watch?v=1Ug6GBNQKBc)
- [UnityでPixel Perfect CameraとCanvasを組み合わせて使用する際の注意点](https://funct.hatenablog.com/entry/2020/09/03/200815)