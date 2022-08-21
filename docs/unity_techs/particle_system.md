# パーティクルシステム


## パーティクルの撒き方の例

実際に撒き方の例を見た方が各項目の意味が分かりやすいので、事例を述べていく。

### 基礎知識・基本的な設定項目

記載のない場合は、Particle System内のParticle Systemの項目をクリックすると出てくる項目。

- パーティクルが出る時間を変える → Durationを変更（この秒数だけパーティクルが生成される。この時間を過ぎてもパーティクルは消えない）
- パーティクルの存在時間を変える（バラつかせる） → Start Lifetimeを変更
- パーティクルの大きさを変える（バラつかせる） → Start Sizeを変更
- パーティクルの密度（数）を変更 → EmissionモジュールのRate Over Timeの値を変更
  - Max Particlesは達していると新たに生成しない数を指し、必ずしも生成される数を意味しない。基本的に適当に大きな値でよい。
- 全体的なスピード感を変えたい → Simulation Speedを変更（カーブなどを指定することも可能）

### 1回だけ撒くか、継続的に撒くか

#### 1回だけ撒く場合

- Loopingのチェックを外す。

- Duration


#### 継続的に撒くが、任意のタイミングで止める

パーティクル生成の是非を制御しているのはEmissionモジュールである。



### パーティクル生成位置にランダム性を持たせる





## 連番アニメーションするパーティクル

### 前提

- パーティクル画像にはTextureとSpriteの両方使えるが、ここではSpriteを使用する。
- 使用するSpriteは1枚のテクスチャを分割したものである必要がある。
- 使用する画像は並んでいたりする必要はなく、同じ画像を複数回出したりもできる。

### マテリアル作成（描画時の合成方法の設定）

マテリアルを作成する。

マテリアルにはMainTexとしてテクスチャを設定する場合が多いが、ここではテクスチャは設定しない。

描画時の合成方法がマテリアルに依存する。

#### 加算合成

新規マテリアルを作成し、シェーダーを、Universal Rendering Pipeline/Particles/Litに設定する。

- Surface TypeをTransparent
- Blending ModeをAdditive
- Color ModeをMultiply

にする。

Color Modeはパーティクルに設定した色と元のテクスチャの色の合成の仕方である。


### ParticleSystemの設定

Particle Systemの設定項目から「Texture Sheet Animation」にチェックを入れ、内容を開く。

ModeをSpritesにする。

### 疑問

パーティクルのColorはパーティクルごとに設定できるようになっているが、Spriteと同様にMaterialPropertyBlockなのか？

→ 多分そう。PerticleSystemコンポーネントの下の方に「Material Property Block is used to modify these values」とある。
パーティクル用のシェーダはParticleSystem専用と考えた方が良さそう。



### 参考ページ

- [ParticleSystemで連番アニメーションをする方法](https://light11.hatenadiary.com/entry/2018/12/06/224926)
- [ParticleのテクスチャアニメーションをSpriteで行う](https://tsubakit1.hateblo.jp/entry/2017/07/11/235900)

## プラスアルファ

- 車輪の跡とかもパーティクルシステムで作れる。

