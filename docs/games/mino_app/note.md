# MinoApp雑記

## Androidアプリ

### 超基本

- Build Settings -> Switch PlatformでAndroidを選択すると選択した段階でスクリプトのコンパイルが行われる。

### つまづきポイント

#### Adaptive Performance

参照ページ：[[Unity] Adaptive Performanceを試してみた](https://qiita.com/mrtm30/items/a33b31bb5d3e85f282dd)

スマホの端末状態（発熱）や電力状態の計測を行えるもの。

とりあえず使わなくても良さそう。


#### Gradleが見つからないとか言われる

「Edit」→「Preferences」→「External Tools」の下の方の「Gradle Installed with Unity(recommended)」のところに「You are missing the recommended gradle.」というWarningが出ていた。

```
C:\Program Files\Unity\Hub\Editor\2021.3.6f1\Editor\Data\PlaybackEngines\AndroidPlayer\Tools\gradle
```

にgradleがあるはずだと書いてあるが、そんなフォルダはない。

Unity Hubを利用してインストールしろと書いてあるが、選べなさそう。

Androidのインストール中に何かエラーが出ていた気もするので、Unity Hubからエディタごと削除→PCを再起動→再インストール。



#### その他

- [【Unity】Unable to find player assembly: XXXX\Temp\StagingArea\Data\Managed\UnityEngine.TestRunner.dll](https://baba-s.hatenablog.com/entry/2022/01/24/150000)

### 参考ページ

- [WindowsとUnityの環境でAndroid実機テストをする方法(2022/2)](https://iucstscui.hatenablog.com/entry/2022/02/21/080000)
- [(公式)Android 環境の設定](https://docs.unity3d.com/ja/2020.3/Manual/android-sdksetup.html)

## 2Dゲームの基礎

### 超基本

- X軸正方向が右側、Y軸正方向が上側。

### カメラ

- 2Dゲームの場合、カメラはOrthographicで、Sizeに設定した値が画面の上端・下端のY座標となる。（横長の場合）
