# Line Renderer

- Positionsに設定した座標を通る線。2D、3Dとも使える。

- Widthはワールド座標上での太さを設定する。1なら1ピクセルではなく1メートルの意味。
- Texture Modeを「Tile」にすると繰り返しUVでテクスチャが貼られる。
    - Uが長さ方向、Vが太さ方向。
    - Vは太さによらず0~1になる。Uは長さ1mごとに0~1のループになる。
    - Uの方が厄介で、太さを1以外にするとテクスチャの縦横比が変わってしまう。Shader側でTiling値を設定できるようにするとよい。