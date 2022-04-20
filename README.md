# ISOC-JP Website repo

## 準備

1. node.js, yarnを準備する  
例: `brew install nodejs yarn autoconf vips`
2. 必要なモジュールをインストールする  
`yarn`
3. ローカルに開発用サーバを起動する  
`yarn start`
4. http://localhost:8000/ にアクセスする

## トラブルシューティング

開発用サーバを起動する時に、環境によっては下記エラーがでるかもしれない。

```
digital envelope routines::unsupported
```

ひとまず起動するだけなら、
NODE_OPTIONSに `--openssl-legacy-provider` を設定する。

```
export NODE_OPTIONS=--openssl-legacy-provider
```
