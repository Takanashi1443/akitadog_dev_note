# ShibaShader

## 前提・全体に関する注意点

ShaderGraphを使用する。

オブジェクトごとにマテリアルのパラメータを変更する場合、Renderer.materialにより取得したオブジェクトごとのマテリアルのパラメータを変更し、
ゲーム終了時に破棄することが前提となる。詳細は[こちらのページ](./../unity_techs/material_for_each_object.md)を参照。

## Sprite用のシェーダ

### 注意点

ShaderGraph上で_MainTexにデフォルト画像を設定する場合、ShaderGraphのプレビューには表示されるがゲーム上では反映されないという困惑する現象が起こる。
Spriteの_MainTexはSpriteRendererのSpriteに設定したSprite画像が適用される。

詳細は[Spriteの仕組み](./../unity_techs/sprite.md)を参照のこと。

### 基本のシェーダ(SpriteShader/Unlit)



## 覚書

