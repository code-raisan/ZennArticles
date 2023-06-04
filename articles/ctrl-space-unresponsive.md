---
title: "Ctrl+Spaceが反応しない場合の対処法"
emoji: "⌨" # アイキャッチとして使われる絵文字（1文字だけ）
type: "tech"
topics: []
published: false
publication_name: "ablaze"
---

VALORANTやってたら、歩きながらジャンプ(Ctrl+Space)できなくて色々触ってたら治ったので何が原因だったか書いていきます

# 結論

PowerToysが原因だった。PowerToysの「プレビュー」のショートカットキーがCtrl+Spaceで重複していた。

(他にもIMEとかが原因だったりすることもあるみたいが、最新のWindows(多分)だと規定でCtrl+Spaceのショートカットは無効だった)

![PowerToys_Preview_File](https://storage.googleapis.com/zenn-user-upload/c518534daad5-20230604.png)

解決方法はこのユーティリティを無効にするか、ショートカットキーを他のものにすればいい
