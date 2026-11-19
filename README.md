# ZEN Study Auto Next

ZEN Studyの授業動画を再生終了時に自動で次に進めてくれます。ハンズフリーで快適に授業を受講できます。

## 機能

- 動画の終了イベントを検知し、設定した待ち時間後に次の動画行をクリック

## インストール方法

1. 最新の [Release](https://github.com/yuichgh/ZenStudyAutoNext/releases) から `.dmg` をダウンロードして開きます。
2. `ZenStudy-Auto-Next-extension.app` を `Applications` にドラッグします。
3. Safariの「設定 → 詳細」でWebデベロッパ向け機能を表示し、「デベロッパ → 未署名の機能拡張を許可」をオンにします。
4. Applicationsからアプリを一度起動し、Safariの「設定 → 機能拡張」で有効にします。

**注意:** DMG化はAppleの署名・公証の代替ではありません。Gatekeeperにより起動を拒否されたり、Safariに拡張が表示されない場合があります。

## ファイル構成

```text
ZenStudy-Auto-Next-extension.xcodeproj/       Xcode プロジェクト
ZenStudy-Auto-Next-extension/                 macOS アプリとアイコン
ZenStudy-Auto-Next-extension Extension/
  Resources/
    manifest.json                           権限と読み込み設定
    core.js                                 動画一覧の判定
    content.js                              終了検知・遷移処理
    popup.html / popup.css / popup.js        設定画面
tests/core.test.cjs                          判定ロジックのテスト
```

拡張機能のソースは `Resources` 配下が正本です。変更後は Xcode で再ビルドし、授業ページを再読み込みしてください。

## 権限・データ

`storage` は設定保存用、`nnn.ed.nico` のホスト権限は動画と一覧の操作用です。拡張ソースは独自サーバーへのデータ送信を行いません。

サイトの画面構造が変わると検出できなくなる場合があります。失敗時は Web インスペクタのコンソールに `[ZEN Auto Next]` の診断が表示されます。別オリジンの動画フレームは追加対応が必要になる場合があります。次の動画ページの自動再生は Safari とサイト側の挙動に依存します。

本拡張は ZEN Study 運営とは関係ありません。確認テストや教材のロックを解除する機能、受講記録を改変する機能はありません。

## ライセンス

本ソフトウェアは [MIT License](LICENSE) のもとで公開しています。

