---
title: "Zennで勉強記録を始めてみた。 #ts勉強ログ001"
emoji: "🍰"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["zenn","TypeScript"]
published: false
---

# Zennについて学ぶ

## Zennすごくない？

今日初めてZennを使ってみてQiitaユーザだった私は驚愕した。CLI機能もこうやってあって、mdで書けるのはQiitaでも同じだったけれど、それ以上にGithubと連携して、PullRequestなどの管理をしながら記事を執筆できる環境は本当に驚いた。今までアップデートを重ねてきた努力の結果なのだろうが、正直驚いた。


## Zennを使ってみた感じ

正直NotionとかQiitaとかConfluenceとかの様々なWiki系記事のいいとこどりの機能追加をしていて、デザイン面でも、機能面を見ても新しく感じるので、今まではNotionに自分だけのWikiを書いてきたのだが、今度からNotionを使用して勉強ログを整理していけたらと思う。

---

...というわけで、これから勉強ログを書いていこうと思う。

# TypeScriptを学ぶ

## 理解できていない点について
TypeScript、Javascriptの型があるAltJSと呼ばれる言語の一種だが、Reactで一通りJavascriptを勉強見たからして、プロとしてしっかりフロントエンドの仕事ができるまでには、自分にとってまだ以下の項目について現時点で全く理解に至っていない。

- 型の指定の仕方
- 型の管理
- パッケージにおける型の操作

また、この勉強ログ以降、Javascript含め、これら言語について以下の部分についてまだ理解していないため、Zenn記事にひたすら記載していく予定である。

- テストフレームワーク Jestなど
- Ajax/Axiosについて
- Next.js
- Vue.js/Nuxt.js
- React再レンダリング問題
- 副作用について
- ECMAScriptについて

理解できたところからそれぞれ、リンクを貼っていきます。

## まず型の指定について

https://zenn.dev/luvmini511/articles/6c6f69481c2d17

まず、型の指定について問題が存在する。`interface`と`type`の問題である。
理解についてはこの上記Zenn記事が面白かった。

読んでいくと、型に名前をつけるという点について同じことが言える。
しかし、`interface`句に関しては変数の`var`のような副作用が存在しているとのこと。

実際に公式ドキュメントを読んでみよう。

https://www.typescriptlang.org/
こちらがTS公式サイト。

https://www.typescriptlang.org/docs/handbook/intro.html
こちらが公式ドキュメント

https://www.typescriptlang.org/docs/handbook/2/objects.html#property-modifiers

うん？でも`?`修飾子でオプションの型として作成することもできるかも。ここの記事で主張されている`interface`の面倒臭さについて書かれているが、`?`修飾子でカバーできるのような気もします。
しかし、名前被りに関しては非常に恐ろしい副作用であることには変わらず、typeのように名前被りしても安全な型を使用する方がTypeScriptらしく書けるのかなとも感じた。

さらに、`type`に関しては`&`演算子によって拡張もできるとのこと。
それならばなおのこと`interface`の出番がないようにも思う。

また、別の記事を見てみよう。
https://zenn.dev/seya/articles/aa94166c977280

非常に深い議論がコメント欄でも交わされているものの、interfaceの安全性が自分の中で腑に落ちるまではtypeを基本的に使っていく方がいいかもしれない。まだ使用もしていないものをここまでごちゃごちゃと話し込むと勉強が進まないので、一旦は
* しっくりくるまでのうちは型宣言はtypeを使っていく方針で
* interfaceの存在は一応知っておく。内容としては
    - `class` `object`にしか使えない
    - 拡張性について存在するので注意すること。
    - 実際使っていくと違いがわかってくるので、後々開発現場でスタートする際に議論したら良い

というわけで、`type`と宣言すればいい。

```typescript
type Foo = "OK" | "NG"; //enum型
type Bar = { //object型
    name : string;
    num : number;
}
```

このような形だろうか。もし間違っていたらコメント頂きたい。

## 型の管理

次に型はどのように配置すればいいのだろうか？

Reduxのコンポーネントの書き方など、わかりやすい置き方やその定義について調べてみる。

まず、このページが非常に参考になった。

https://zenn.dev/ogakuzuko/articles/react-typescript-for-beginner

もうここに書かれていることが全てだった。すごい勉強になった。

## パッケージによる型の操作

基本的にReactの場合は
```typescript
import React from "react";

```

これで型まで全て入るようになっている。
具体的にそうする方法については、パッケージ配布のレベルなので、今の自分にはレベルが足りない。
どうやら`.d.ts`ファイルにぶっ込んでると思われるが、今後調査していく。

以上、今日の調査は終わり。
次回は、Qiitaのこちらのチュートリアルを行なっていく。

https://qiita.com/uhyo/items/e2fdef2d3236b9bfe74a

