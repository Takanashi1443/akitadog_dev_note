# トラブルシューティング集

## Unity仕様

### コンポーネントの横にチェックボックスが出ない

Start、Update、Awakeなど、MonoBehaviourの機能に関連する関数を1つも記載していないとチェックできなくなる。

### ScriptableObjectの名前が見つからないとか言われる

アセットの名前と(ScriptableObject).nameとを一致させないと宜しくない。
