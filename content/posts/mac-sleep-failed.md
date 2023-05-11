---
title: "【Mac】Intel MacBookのスリープ復帰に失敗する問題"
date: 2023-05-12T06:33:05+09:00
tags: ["Mac"]
---

現在愛用しているサブ機の Intel MacBook Air (2019) が
スリープから復帰に失敗する問題が発生しました。

左上の Apple マークのスリープボタンや本体を閉じてスリープしたあと、
数時間経過して作業を再開しようとすると、完全に電源が落とされた後に
再起動したような動作になります。

## とりあえずの応急処理

周辺機器を抜いたりして色々試したのですが、解決にならず。

そして唯一見つけたのがこの Reddit の投稿でした。

[Sleep wake failure in EFI - Reddit](https://www.reddit.com/r/MacOS/comments/dme38s/sleep_wake_failure_in_efi/)
[Error after having hard drive replaced. - Apple Community](https://discussions.apple.com/thread/250469185)

Reddit の投稿に貼られた Apple Community のリンクを見ると、

Terminal.app(ターミナル)を開いて、

`sudo pmset -a standby 0`

このコマンドを実行するように書かれていました。

そして実行してみると何と通常通り動いてしまいました...

## 原因は修理？

上記の記事にあるように、修理歴があると発生する問題のようです。

この Mac は TouchID が動作しない問題から、
マザーボードごと交換してもらったことがあります。

そこから発生したことは不明ですが、原因はそのぐらいしか見当がつきません。

## バッテリー問題

どうやらこのコマンドで解決はしましたが、
バッテリーの消費が早くなるようです。

## その後について

応急処置的ではありますが、その後は普通に動作してくれています。

何かあったらまた追記しておこうと思います。
