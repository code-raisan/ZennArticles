---
title: "【Cloudflare Access/Cloudflare Zero Trust】GitHubのOrg名で認証するときにハマった話"
emoji: "🔥" # アイキャッチとして使われる絵文字（1文字だけ）
type: "tech"
topics: ["cloudflare", "cloudflare access"]
published: false
publication_name: "ablaze"
---

開発用サーバーへのアクセス認証をつける際にCloudflare AccessでGitHubのorg名で判定する用にしようと設定していたら、認証ができなくてハマったのでその原因と対処法を書いていきたいと思います。

# 結論

認証時に使うGitHub OAuthの連携時にorgへのアクセスを許可していなかった。GitHub OAuthは連携時にorgへアクセスする場合はorgへのアクセスを別途選択しないといけない。そして、以前は自分だけで利用してたのでorgを選択していなかったため気づけなかった。
