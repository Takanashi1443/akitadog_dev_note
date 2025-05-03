# ベストプラクティス集

## データ設計

### 固定個数のモノにいくつかの数値を紐づけたい

難易度Easyなら被ダメージ半減、経験値2倍、Hardなら被ダメージ1.2倍、経験値0.8倍…など。
ソースコードに直接書くにしては種類が多いが、ScriptableObjectによるデータベースを作るほどではない（中身を確認しやすいようにしたい）もの。

__⇒列挙型とし、列挙型をキーとする辞書を作る。__

<details>

例えば、音楽の再生速度をいくつかから選択させる時

(enumを定義する側)

```

namespace DrumTrainGame
{
	/// <summary>
	/// 楽曲の再生速度の列挙体。
	/// </summary>
	public enum SpeedRate
	{
		Undefined,
		VerySlow,
		Slow,
		Medium,
		Fast,
		VeryFast,
	}

	public static class SpeedRateSettings
	{
		public static readonly Dictionary<SpeedRate, string> speedAlias = new Dictionary<SpeedRate, (float, string)>
		{
			{ SpeedRate.Undefined,	"ND" },
			{ SpeedRate.VerySlow,	"75%" },
			{ SpeedRate.Slow,		"90%" },
			{ SpeedRate.Medium,		"100%" },
			{ SpeedRate.Fast,       "110%" },
			{ SpeedRate.VeryFast,   "125%" },
		};

		// 1段階遅い速度を取得
		public static SpeedRate GetSlowerSpeed(SpeedRate current)
		{
			if (current == SpeedRate.Undefined || current == SpeedRate.VerySlow)
				return current;

			return current - 1;
		}

		// 1段階速い速度を取得
		public static SpeedRate GetFasterSpeed(SpeedRate current)
		{
			if (current == SpeedRate.Undefined || current == SpeedRate.VeryFast)
				return current;

			return current + 1;
		}
	}
}

```

(利用する側)

```

text = SpeedRateSettings.speedAlias[spdRate]; // 再生速度を表す文字列を取得

```

辞書を複数用意すれば、後から紐づける情報を増やすこともできる。

</details>

## シーン設計

### モーダルダイアログ的な役割のUIを作成し、その結果を受け取りたい

例えば、音楽ゲームにおける楽曲選択UIを複数シーンで使用したいなど。極力疎結合（互いの存在を知らない）にしたい場合。

__⇒UI全体をプレハブで作成し、結果をUniRxのMessageBroker.Default.PublishとReceiveで渡す。__

(MessageBroker.Defaultの詳細)

<details>

通常の購読関係（IObservableのSubscribeとSubjectのOnNext）によるメッセージ伝達と異なり、MessageBroker.DefaultのPublishは、それをReceiveしている全てのコンポーネントにメッセージを渡すことができる。

内部的にはMessageBroker.Defaultはシングルトンのインスタンスである。

MessageBroker.Default.Publish(x)で、xの型を自動で判定し、その型をMessageBroker.Default.Receiveで受け取っているコンポーネント全てにメッセージを渡す。

型が同じ場合、関連させるつもりのないコンポーネントにもメッセージが渡ってしまう一面もあるが、型をモーダルダイアログ固有のenumなどにすれば良い。ScriptableObjectも渡せるため、楽曲を選択して楽曲のScriptableObjectを渡すといったこともできる。

受け取り側の実装方法は下記の通り。

```

// MusicMaster が publish されたら再生
MessageBroker.Default.Receive<MusicMaster>()
    .Subscribe(OnMusicSelected)
    .AddTo(this);

// 呼ばれる関数
public void OnMusicSelected(MusicMaster master)
{
    ...
}

```

AddTo(this)は、GameObjectが破棄された時に登録解除される仕組み。
Subscribeされるのが1回だけであればこれで良い。

購読・破棄を繰り返す場合は、Subscribe()の戻り値のIDisposableをメンバなどで保持しておき、IDisposable.Dispose()で破棄する。

</details>

(Prefabの構造の指針)

<details>

ルートにCanvasと、モーダルダイアログのControllerをアタッチすると良い。部品には制御を行うスクリプトはアタッチせず（せいぜい自身の見た目を装飾するコンポーネントのみ）、ルートのControllerから全てのUIパーツを制御する。

</details>

## 動作

### 固定秒数のウェイトを入れたい

例えばSceneManagerがStart関数で色々動かすが、その前に数秒待ちたいなど。

__⇒DoTweenのDelayedCallを使う__

```

(using)
using DG.Tweening;

(クラス内)
DOVirtual.DelayedCall(0.5f, () => {
    HogeFunction();
});

```

