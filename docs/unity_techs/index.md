# Unityのテクニック

## 個別ページ

- [Spriteの仕組み](./sprite.md)
- [初期化関数の使い分け(Awake, OnEnable, Start)の使い分け](./awake_and_start.md)
- [オブジェクトごとにマテリアルのパラメータを変更](./material_for_each_object.md)
- [パーティクルシステム](./particle_system.md)

## アセットの仕様・設定など

### ドット絵をぼやけさせずに拡大表示させる

- 画像のインポート設定の「Filter Mode」を「Point(no filter)」にする。
- [参考ページ](https://qiita.com/Upon/items/2f6a9378e5eee3a8140a)

### ドット絵をタイル状に読み込む

#### インポート設定

タイル状に読み込んで扱える画像はスプライトに限られる。

（3DオブジェクトのテクスチャなどもUVを指定して一部のみを扱うことはできるが、ここではスプライトについてのみ説明する）

Texture TypeをSprite(2D and UI)にする。

Sprite Modeを Multipleにする。

Sprite Editorを開くと分割する方法を選べる。（Sprite Editorを開くボタン自体は元々あるが、内容が変わる）

Sprite Editorウィンドウの▼ボタンを押すと、スプライトの分割方法を選ぶことができる。

Grid By Cell Sizeを選び、1枚あたりのピクセル数を入力し、Keep Empty Rectsにチェックを入れ、Sliceを押すと画像全体がその大きさで分割される。

分割した画像はそれぞれをスプライトとしてSprite Rendererなどで表示させられる。



#### 参考ページ

- [【Unity】スクリプトからMaterialをオブジェクトごとに変更](https://haraken.hatenablog.com/entry/2018/07/03/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%97%E3%83%88%E3%81%8B%E3%82%89Material%E3%82%92%E3%82%AA%E3%83%96%E3%82%B8%E3%82%A7%E3%82%AF%E3%83%88%E3%81%94%E3%81%A8%E3%81%AB%E5%A4%89%E6%9B%B4)
- [【Unity】Renderer.materialで取得したマテリアルは自分で破棄しないとリークする話](https://light11.hatenadiary.com/entry/2019/11/03/223241)

