# 入力システム

## 参考ページ

-[InputSystem](./../builtin_assets/inputsystem.md)

## 概念

分からなくなるので、シーンごとに入力を受け取る内容を変えるようなことはせず、受け取る入力群の種類は1つだけ（(ゲーム名)Actions）とする。

InputReceiverという、入力を受け取るGameObjectをシーン上に用意する。

InputReceiverはInputSystemを使って作成したアクションのインターフェイスを継承して入力を受け取ることができ、また、UniRxのイベント発行の機能を持つ。

入力によって動作するGameObject群はInpurReceiverの発行するイベントを購読する。

入力を一括で無効にする場合など、InputReceiverは受け取った入力を元にイベントを発行するかどうかを判断する機能を持っても良い。それにあたり、SceneManagerと相互に参照したりしても良い。

## 具体的な実装

- InputSystemアセットを作成する。名前は(プロジェクト名)InputControlsとする。

- InputSystemアセット内に受け取る入力群を定義する。入力郡の名前は(プロジェクト名)Actionsとする。

- Generate C# Class → Applyにより(プロジェクト名)Actionsに対応するスクリプトを生成する。(プロジェクト名)InputControls.I(プロジェクト名)Actionsというインターフェイスが生成され、それを継承することでスクリプトが入力を受け取れるようになる。

- シーン内に「InputReceiver」というGameObjectを配置する。

- InputReceiverに、シーンごとに作成するInputReceiverスクリプトを作成し、アタッチする。
