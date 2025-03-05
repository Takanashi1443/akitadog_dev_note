# 用語

## 命名規則

ここでは、混乱を防ぐために、Unityにおける特定の用語の用途をその用途に限定するために定める命名規則を述べる。

「限定使用」とは、排他的に使用することを指す。

`MasterおよびCatalog`

:   XxxxMasterやXxxxCalalogの名前でスクリプト名、クラス名に使用する。
    マスタデータおよび、マスタデータを集めたものを指す。
    [CSVとScriptableObjectによるデータベース](./csv_so_database.md)で使用する。
    RecordおよびDataBaseと同じような意味合いだが、これらの用語はより一般的に使うため避けている。

`SaveOrganizer`

:   XxxxSaveOrganizerのようなクラス名で、[セーブ・ロード](./save.md)で使用する。
    セーブ・ロードに関してセーブデータファイルとのやりとりを行う。

`SaveOperator`

:   XxxxSaveOperatorのようなクラス名で、[セーブ・ロード](./save.md)で使用する。
    SaveOrganizerからデータを構成するための情報を受け取り、利用できる形に変換する。
    また、セーブデータに対する処理やアクセサを提供する。



## 参考サイト

