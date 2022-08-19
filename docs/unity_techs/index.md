# Unityのテクニック

## 個別ページ

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



### パーティクルシステム

#### 前提

パーティクル画像にはTextureとSpriteの両方使えるが、ここではSpriteを使用する。

#### マテリアル作成（描画時の合成方法の設定）

マテリアルを作成する。

マテリアルにはMainTexとしてテクスチャを設定する場合が多いが、ここではテクスチャは設定しない。

描画時の合成方法がマテリアルに依存する。

新規マテリアルを作成し、シェーダーを、

- 加算合成したい場合：Mobile/Particles/Additive


に設定する。

#### 

#### 参考ページ

- [ParticleSystemで連番アニメーションをする方法](https://light11.hatenadiary.com/entry/2018/12/06/224926)


