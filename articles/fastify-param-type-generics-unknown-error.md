---
title: "TypeScript環境のFastifyでパラメータを受け取る時にunknown型で取れない場合"
emoji: "🚧"
type: "tech"
topics: ["fastify", "typescript"]
published: true
---

:::message
注意: TS初心者によるしょうもないミスです
:::

ドキュメントを見ながら(見落とし)パラメータの型定義をしていたのですが、何故か`const { user } = request.query`とすると`unknown`だから取れないとエラーを吐かれ2週間。
VALORANTやったり原神をやったりして現実逃避をしていたのですがやっとこさ解決できました。

```ts:問題のコード
app.get<{
    Querystring: {
        user: string;
    }
}>("/test", async (request: FastifyRequest, reply: FastifyReply) =>{
    const { user } = request.query;
    reply.type(utils.ApplicationJson).code(200).send({ test: user });
});
```

# 結論

`unknown`で定義されている型定義で上書きしてしまっていた。

```diff ts
("/test", async (
-    request: FastifyRequest, 
+    request,
    reply: FastifyReply
) => {}
```

とするとあっさり治った。(ドキュメント通りにやった結果)

# どうしてもこうなった

`request: FastifyRequest`ここが問題でした。`FastifyRequest`には`Querystring: unknown`とするように定義されていたようです。
型定義ファイルとにらめっこしたのですが型定義ファイルをたどった結果ジェネリクスぽかったのでてっきり`app.get<{}>`のジェネリクスを吸って定義しているのだと思って大丈夫だと思っていた。
どうやら違ったようだ。。。。。。。。
関数の前においたジェネリクス(?)は無視されるみたい

ドキュメントをしっかりと読んだ結果、あれ。。。。`FastifyRequest`ついてなくね??????????
そうですVSCodeの補完で探して型を当てていたのでエラー出ないし名前的にも大丈夫そうだと思ってたんですよ。。。。
素直にドキュメントに沿っておくべきだったと反省

あれそういえば型定義ファイルにあったジェネリクス。。。。。

```ts
request: FastifyRequest<{ Querystring: { user: string } }>
```

あ、、、、通った。。。。。。。
まあ確かに引数に指定してる型が急に関数のところについてるやつを吸うわけないか
というわけで色々とハマってしまった
ドキュメントちゃんと読もう！！！
終わり！！ 最後までこんな駄文を読んでいただきありがとうございました！！！!
