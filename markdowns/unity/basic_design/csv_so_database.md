# CSVとScriptableObjectによるデータベース

様々なゲームで、ローカルで固定のデータベースを持たせたいことがある。
例えば、RPGにおける敵キャラのデータベース、リズムゲームにおける楽曲情報のデータベース、カードゲームにおける、カード名、画像（への参照）、効果など……。

また、これらのデータベースは相互に連携する場合がある。
例えば、敵キャラがアイテムをドロップする時、アイテムのデータベースを参照して指定するなど……。

少数のデータならアセットで作成したり、定数配列にしたりしても良いが、RPGにおけるアイテムなどはこのような方法を取ることは難しい。

そのようなデータベースを、CSVとScriptableObjectを使ったデータベースを使って実現する。

## 用語

まず、この方法で作成するデータベースにおいて以下の用語を限定使用する。

`Master`

:   マスタデータとなるScriptableObjectクラス。
    アイテム1件、敵キャラ1件など、データベースにおけるレコード1件を指す。

`Catalog`

:   単一種類のマスタデータをリストなどの形で保持するGameObjectクラス。
    また、CSVファイルからマスタデータを作成する関数「Build」を持つ。

## 要件・設計（基本編）

この仕組みは、下記のような要件を実現できるように設計される。

### CatalogはMasterのリストを保持し、またそれをcsvファイルから形成できる

![CatalogはMasterを保持し、またそれをcsvファイルから形成できる](./img_csv_so_database/catalog_has_masters_and_can_build_from_csv.png)

### 各CatalogはCatalogBuilderによってビルドされる

![各CatalogはCatalogBuilderによってビルドされる](./img_csv_so_database/catalogs_are_built_by_catalog_builder.png)

### Catalogsはゲーム起動時に生成され、各シーンのGameObjectから参照される

![Catalogsはゲーム起動時に生成され、各シーンのGameObjectから参照される](./img_csv_so_database/static_catalogs_are_referred_by_gameobjects.png)

### 要件の整理・補足

- Catalogは自身のCSVファイルへのパスを持たない。
- CatalogBuilderはCSVファイルへのパスを持つ。CatalogBuilderシーンで各Catalogプレハブの中身を更新するのに使用され、ゲームには含まれない。

## 実装（基本編）

### ゲーム起動時にCatalogsを生成する



## 参考サイト

- [【備忘録】ScriptableObjectとCSVの連携・「転生女騎士、アパートに住む【放置ゲーム】」の作り方（3）【Unity】](https://note.com/yamasho55/n/n04bd2f6d136d)
- [【Unity】ゲーム中に常時必要なGameObjectがどのシーンから始めても存在するようにしてみよう](https://www.urablog.xyz/entry/2018/02/11/164734)