# オブジェクトごとにマテリアルのパラメータを変更

オブジェクトが受ける効果をマテリアルのパラメータで表現したいことは多いが、マテリアルのパラメータ変更にあたっては注意が必要である。

マテリアルの取得方法は2つあり、それぞれ注意が必要となる。

- Materialアセットそのもののパラメータを設定する場合 → そのマテリアルを使用している全てのマテリアルのパラメータが変更される
- GameObjectごとに異なるパラメータを設定する場合 → 個別に設定する方法があるが、内部でマテリアルを複製しており、メモリの開放が必要

Prefabとして複数オブジェクトを使用する場合、基本的には後者の方法が必要になる。
ここではその方法について説明する。

## GameObjectごとに異なるパラメータを設定する

```

GetComponent<Renderer>().material

```

で、そのゲームオブジェクトのマテリアルが取得できる。

しかしこの時内部ではマテリアルが複製されており、そのままゲームを終了するとメモリリークする。

取得したマテリアル（ここではm_material）に対し、

```
    private void OnDestroy()
    {
        if (m_material != null) {
            Destroy(m_material);
        }
    }

```

などとし、ゲームオブジェクトの破棄時にマテリアルを破棄する。

## 備考

```

GetComponent<MeshFilter>().mesh

```

でオブジェクトごとにメッシュを取得できるが、その時も同様の複製が行われており、開放が必要。

## 参考ページ

- [スクリプトからマテリアルをオブジェクトごとに変更](https://haraken.hatenablog.com/entry/2018/07/03/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%97%E3%83%88%E3%81%8B%E3%82%89Material%E3%82%92%E3%82%AA%E3%83%96%E3%82%B8%E3%82%A7%E3%82%AF%E3%83%88%E3%81%94%E3%81%A8%E3%81%AB%E5%A4%89%E6%9B%B4)
- [【Unity】Renderer.materialで取得したマテリアルは自分で破棄しないとリークする話](https://light11.hatenadiary.com/entry/2019/11/03/223241)

