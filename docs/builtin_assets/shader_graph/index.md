# ShaderGraph

## 導入

- Package Managerからインストール。
- Assets→Create→Shader Graphから新規作成できる。

## 引っかかる点

- Built-InのLit ShaderとUnlit Shaderのうち、Lit Shaderは物理ベースシェーダ（PBR）の原型を、Unlit Shaderは光の影響を受けないシェーダを作ってくれる。
- Ctrl+Sで保存できない。ウィンドウ左上の「Save Asset」で保存する。

## Unlit Shader基本事項

新規作成するとVertexとFragmentがつながった雛形が作られる。

Vertexは変形に関するもので、色の変更（グラデーションなど）を作りたい場合はFragmentに入る値のみ変えればよい。

### 半透明

FragmentにAlpha値を追加した上でBlendの設定をAlphaにすると半透明にできる。
（参考ページ:[Unity ShaderGraph レシピ #9 半透明](https://qiita.com/Teppy/items/06baca3b5532ec006f03)）

## 具体例

- [矢印模様 (LineRenderer)](https://zenn.dev/r_ngtm/books/shadergraph-cookbook/viewer/recipe-linerenderer-arrow)


## 参考ページ

### 全体

- [ShaderGraphまとめ](https://shadergraph.sanukin.net/)
- [ShaderGraphのインストール](https://shadergraph.sanukin.net/shadergraph%E3%81%AE%E3%82%A4%E3%83%B3%E3%82%B9%E3%83%88%E3%83%BC%E3%83%AB/)
