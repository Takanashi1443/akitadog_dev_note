# 初期化関数（Awake, OnEnable, Start）の使い分け

## 違い

### Awake

- GameObjectがアクティブになった瞬間に1回だけ呼ばれる。
- スクリプト自身が非アクティブでも呼ばれる。
- OnDestroyと対応していると言えそう。

### OnEnable

- スクリプトが有効になった時に何度でも呼ばれる。
- OnDisableと対応している。

### Start

- Update関数を行う時、それが最初のUpdateであれば1回だけ呼ばれる。

### 順番

スクリプトがアクティブな状態でGameObjectを生成した時の実行順序は

1. Awake
1. OnEnable
1. Start

となる。

## コンポーネントの参照に関する使い分け

- 自身のGameObjectにアタッチされた他コンポーネントを参照する時は、Awakeを使用する。
- 他のGameObjectにアタッチされた他コンポーネントを参照する時は、StartかOnEnableを使用する。

## 参考ページ

- [【Unity検証】AwakeとStartとOnEnableの呼ばれ方を調べてみた](https://dkrevel.com/unity-explain/how-to-call-start-awake-onenable/)