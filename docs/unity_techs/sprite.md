# Spriteの仕組み

## 画像をSpriteとして扱う（インポート設定）

スプライトとして扱う場合、画像のインポート設定のTexture Typeを「Sprite(2D and UI)」にする。

Unityのプロジェクトを2D設定で作成するとデフォルトでこのインポート設定になる。

インポート設定がDefaultだとSpriteとしては扱えない。

### ドット絵のインポート

更に、ドット絵をぼやけさせずに拡大表示させたい場合は画像のインポート設定の「Filter Mode」を「Point(no filter)」にする。

- [参考ページ](https://qiita.com/Upon/items/2f6a9378e5eee3a8140a)

### 1枚の画像をタイル状に分割してインポート

タイル状に読み込んで扱える画像はスプライトに限られる。

（3DオブジェクトのテクスチャなどもUVを指定して一部のみを扱うことはできるが、ここではスプライトについてのみ説明する）

インポート設定のSprite Modeを Multipleにする。

Sprite Editorを開くと分割する方法を選べる。（Sprite Editorを開くボタン自体は元々あるが、内容が変わる）

Sprite Editorウィンドウの▼ボタンを押すと、スプライトの分割方法を選ぶことができる。

Grid By Cell Sizeを選び、1枚あたりのピクセル数を入力し、Keep Empty Rectsにチェックを入れ、Sliceを押すと画像全体がその大きさで分割される。

分割した画像はそれぞれがSpriteアセット扱いとなる。

## 表示の仕組みとShaderGraphを使用する際の注意

SpriteRendererにはSpriteという項目があり、そこにSpriteとしてインポートした画像を設定することができる。

これにより、MeshRendererコンポーネントがレンダリングを担うオブジェクトと異なり、異なる見た目のSpriteを同じMaterialで表示させることができる。

このSpriteに設定した画像は、シェーダの_MainTexにも使用され、逆に言えばSpriteの_MainTexにはこのSpriteの画像が使用されるため、

Sprite用のマテリアルの_MainTexをマテリアルの設定項目から設定しようとしても反映されない。

この仕組みはMaterialPropertyBlockと呼ばれる。

（ShaderGraphなどの上でもデフォルトの_MainTexを設定することができ、ShaderGraphのプレビューではそれが表示されるが、ゲーム上では反映されない）

ちなみに、_MainTex以外のパラメータをオブジェクトごとに設定するにはMesh Rendererと同様、[ゲームオブジェクトごとのMaterialを作成](./material_for_each_object.md)する必要がある。

一方、SpriteRendererの設定項目であるColorはMaterialPropertyBlockではないようで、ShaderGraphで_Colorという変数を設けてもColorとは連動しないし、ShaderGraphの内容によらず

スプライトは描画結果にColorを乗算したものが描画される。（例えばAlphaを下げれば半透明になるし、Colorを赤にすれば赤成分のみ残る）

ShaderGraphで使用するColorの値をオブジェクトごとに変えるにはやはり[ゲームオブジェクトごとのMaterialを作成](./material_for_each_object.md)する必要があるようだ。

[このページ](https://forum.unity.com/threads/presence-of-vertex-color-node-in-sprite-shader-graph-always-tins-the-entire-sprite.769706/)のQAでもそう結論づけている。

備考：Imageコンポーネントの場合はVertex Colorというノードにより使用できるらしい……？

## Spriteをシーン上に配置する時の挙動

Spriteは、ProjectビューからHierachy上やシーンビュー上に配置することができる。

これは、デフォルトのSprite用マテリアルをマテリアルに、当該のSpriteをSpriteRendererのSpriteに設定したゲームオブジェクトをCreateすることと等しい。

