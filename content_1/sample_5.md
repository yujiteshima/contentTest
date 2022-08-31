---
title: 'Next.jsでmarkdownブログを表示する'
date: '2022-06-15'
description: 'Next.jsでmarkdownファイルを利用したブログの構築手順を解説しています。'
image: gopher.svg
slug: 'sample_4'
categories: ['golang']
blogType: 'myblog'
url: ''
---

Next.js を使って Markdown のブログサイトの作成します。
APIを叩くと用意されたjsonファイルを取得できるAPIを作成しようと思いますので、表示します

## Next.js の準備

### APIを叩く

データを取得できるところまでは見てみたいです。

### コードブロックの見え方を確認したいです。
```js: test.js
const hello = () => {
    console.log("samaple");
}
```

### GFM
| foo | bar |
| --- | --- |
| baz | bim |

~~Hi~~ Hello, world!

- [x] foo
  - [ ] bar
  - [x] baz
- [ ] bim