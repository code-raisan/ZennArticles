---
title: "Ctrl+Spaceが反応しない場合の対処法"
emoji: "⌨"
type: "tech"
topics: []
published: true
publication_name: "ablaze"
---

VALORANTやってたら、歩きながらジャンプ(Ctrl+Space)できなくて色々触ってたら治ったので何が原因だったか書いていきます。

# 結論

エンジニアなら入れてる人が多いであろう、PowerToysが原因だった。PowerToysの「プレビュー」のショートカットキーがCtrl+Spaceで重複していた。

(他にもIMEとかが原因だったりすることもあるみたいが、最新のWindows(多分)だと規定でCtrl+Spaceのショートカットは無効だった)

![PowerToys_Preview_File](https://storage.googleapis.com/zenn-user-upload/c518534daad5-20230604.png)

解決方法はこのユーティリティを無効にするか、ショートカットキーを他のものにすればいい。

では、良いゲームライフを！
