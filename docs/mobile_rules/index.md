# モバイルゲーム開発

## Android端末

### 事前にやること

#### JDK、Android SDK、NDK、Gradleをインストールする

Unity HubでAndroid環境をインストールするとインストールされるが、うまくインストールされていない場合もあり注意。

「Edit」→「Preferences」→「External Tools」の「Android」の欄にあり、インストールがうまくいっていない場合は警告が出る。

インストールがうまくいっていない場合はそのバージョンのUnityエディタごと再インストールするのが良さそう。

#### Package Nameを設定する

「Build Settings」→「Player Settings」または「Project Settings」→「Player」（どちらも同じ画面になる）で、Company NameとProject Nameを変更する。

Company Nameは英語のAtelier LithographではなくIshiyomiKoubouとしている。

#### Android端末を開発者モードにする

開発者モードにしていないと後述のようなことができない。

ビルド番号を7回タップすると開発者モードにできる。

端末によっては他の方法が必要になることもあるようだ。

OFFにする時は、「機能」→「システム」に「開発者向けオプション」という項目が出るので、そこからOFFにできる。

#### USBデバッグを有効にする

開発者向けオプション内に「USBデバッグ」のON/OFFを切り替える項目があるので、ONにする。

### (方法1)実機にインストールせずにテスト（Build and Run）

- USBケーブルでAndroid端末とPCを接続する。

- Unity上でBuild and Runを実行。

### (方法2)実機にインストールしてテスト

Android SDKのadb(Android Device Bridge)という機能を使ってインストールする。

- Unity上でビルドし、apkファイルを保存する。
- External Tools(上述)のAndroid SDKの場所をコピーし、エクスプローラで開く。その中の「platform-tools」フォルダに入る。
- そこでコマンドプロンプトを開く。
- コマンドプロンプトで以下のコマンドを実行。

```

adb install (apkファイルのパス)

```


### 参考ページ

- [UnityがインストールしたAndroid SDKをそのまま使う(2022/2)](https://blog.yucchiy.com/2022/02/using-androidsdk-installed-by-unityhub/)
- [Unityで開発したゲームの実機テストを行う方法(2021/3)](https://miyagame.net/unity-real-machine-android/)

