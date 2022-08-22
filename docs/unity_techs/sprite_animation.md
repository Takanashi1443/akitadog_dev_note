# スプライトアニメーション

## アプローチ

- アニメーションを作るのはAnimationClipがやりやすい
- 一方、AnimatorControllerのステートマシンによる管理は難しい

ため、

- AnimatorControllerはあくまでもAnimationClipの登録場所と割りきる
- Script上でアニメーションIDを設定するとそのアニメーションになる

という方針とする。

以下のページの方法にかなり準拠している。

- [StateMachineは人類には早すぎる](https://zenn.dev/nekomimi_daimao/articles/1feb0dc803ff5d)



## 参考ページ

- [2Dのスプライトアニメーション再生方法まとめ-前編-](https://qiita.com/Gok/items/ed8093d54aabd7a62615)
- [StateMachineは人類には早すぎる](https://zenn.dev/nekomimi_daimao/articles/1feb0dc803ff5d)
