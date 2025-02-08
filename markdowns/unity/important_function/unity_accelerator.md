# Unity Accelerator

## インストール(初回)

![インストール場所](./img_unity_accelerator/install_location.png "インストール場所")

- Installation Directory -> プログラムを置く場所。Program Filesのままで良い
- Storage Directory -> データを置く場所。SSDの分かりやすい場所。ここではD://UnityAccelerator

![Protocol Config](./img_unity_accelerator/protocol_config.png "Protocol Config")

- Accelerate Unity Collaborateは外す

![Security Config](./img_unity_accelerator/security_config.png "Security Config")

- 個人開発でサーバとして使わない場合は「Allow Insecure access with NO encryption」で良い

![Credentials](./img_unity_accelerator/credentials.png "Credential")

- UsernameとPassword。普段は自動ログインなので忘れがち。メモっておく。

![Install finished](./img_unity_accelerator/install_finished.png "Install finished")

最後にサーバーのIPアドレスが出るので控えておく。
自分の場合は192.168.1.12:10080にアクセスするとダッシュボードが見られる。

## プロジェクトへの導入

![Company and Product Name](./img_unity_accelerator/company_and_product_name.png "Company and Product Name")

CompanyNameとProductNameを最初に変えた方が良さそうな気がする。

![Project Settings](./img_unity_accelerator/project_settings.png "Project Settings")

Project Settings -> Editor -> Cache Serverと進み、

- Modeを「Enabled」
- IP addressを先程のアドレス

![Cacheserver Connected](./img_unity_accelerator/cacheserver_connected.png "Cacheserver Connected")

- 接続するとUnityEditorの右下にDBっぽいアイコンが出る

![Metrics Before](./img_unity_accelerator/metrics_before.png "Metrics before connecting project")

![Metrics After](./img_unity_accelerator/metrics_after.png "Metrics after connecting project")

何かしらのアセットをインポートした時にDownload into Cacheの数値が増えていればOK

## 備考
Unity 2019.3からアセットのインポート周りがAsset Pipeline2という仕組みに変わり、
これまでローカルキャッシュサーバーという仕組みがあったのが無くなり、代わりにUnity Acceleratorを使うようになった。

## 参考リンク
- [【Unity】Unity Accelerator の基本的な使い方](https://baba-s.hatenablog.com/entry/2020/09/14/090000)
これが一番詳しかった。
- [Unity 2019.3以降のアセットインポートをUnity Acceleratorで速くする](https://korinvr.com/blog/2020/02/09/)
- [Unity開発を高速・快適にするためのメモ](https://tech.framesynthesis.co.jp/unity/qol/)
