# frame-tools

Steam Frame で VRChat をもっと楽しむための小さなツール集です。どれも Frame の Konsole に 1 行貼るだけで入り、sudo は使いません。

## ツール

- **[frame-vitals-osc](https://github.com/cympfh/frame-vitals-osc)**: 電池残量・充電中かどうか・本体の温度をアバターに届けます。電池メーターや「熱いと汗をかく」アバターが作れます。
  ```sh
  curl -fsSL https://raw.githubusercontent.com/cympfh/frame-vitals-osc/main/install.sh | bash
  ```
- **[frame-gaze-gestures](https://github.com/cympfh/frame-gaze-gestures)**: 長いまばたきや上を見るなど、目の動きでアバターのギミックを切り替えます（frameeyeosc が必要です）。
  ```sh
  curl -fsSL https://raw.githubusercontent.com/cympfh/frame-gaze-gestures/main/install.sh | bash
  ```
- **[frame-doctor](https://github.com/cympfh/frame-doctor)**: 温度・電池・SteamVR・入っているツールなどを 1 コマンドで点検し、困りごとの原因を探します。
  ```sh
  curl -fsSL https://raw.githubusercontent.com/cympfh/frame-doctor/main/install.sh | bash
  ```
- **[vrc-wrist-notifier](https://github.com/cympfh/vrc-wrist-notifier)**: VRChat で誰かが来た・帰った、招待が届いた、などを視界に小さく知らせます（VRChat の PC 側にも入れます。手順はリンク先へ）。
  ```sh
  curl -fsSL https://raw.githubusercontent.com/cympfh/vrc-wrist-notifier/main/frame/install.sh | bash
  ```

**いっしょに使うのがおすすめ**: ささけん＠さんの [Steam Frame アプリ](https://github.com/sasaken1102r/frame)（視線を VRChat に送る frameeyeosc、日本語キーボード、マイク調整、性能オーバーレイなど）。メニューから選んで入れられます。
```sh
curl -fsSL https://frame.sasaken1102s.net | sh
```

## VRChat で使う

アバターの Expression Parameters に、使いたいものを同じ名前で追加します（OSC を有効にしておく）。

| パラメーター | 型 | 送るツール | 中身 |
|---|---|---|---|
| `FrameBattery` | Float | frame-vitals-osc | 電池残量（0〜1） |
| `FrameTemp` | Float | frame-vitals-osc | 本体の温度（30 °C で 0、95 °C で 1） |
| `FrameCharging` | Bool | frame-vitals-osc | 充電中 |
| `GazeToggle` | Bool | frame-gaze-gestures | 長いまばたき 2 回でオン・オフ |
| `GazeLookUp` | Bool | frame-gaze-gestures | 上を 1 秒見ると 0.5 秒だけオン |
| `GazeWinkLeft` / `GazeWinkRight` | Bool | frame-gaze-gestures | ウインクで 0.5 秒だけオン |
| `GazeLongBlink`、`GazeLookDown` / `GazeLookLeft` / `GazeLookRight` | Bool | frame-gaze-gestures | 最初はオフ。設定でオンにすると使えます |

frame-doctor と vrc-wrist-notifier はアバターのパラメーターを使いません。

非公式のツールで、Valve や VRChat とは関係ありません。
