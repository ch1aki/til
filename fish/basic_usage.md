### 見た目などの設定変更

`fish_config`コマンドを実行すると、ブラウザで設定ページが開く。

### 環境変数を指定して実行したい時

bashとかでやる、`HOGE="fuga" echo $HOGE`のfishでのやり方。

```
$ env HOGE="fuga" env
➜  ~ env HOGE=fuga env
(---- snip ----)
HOGE=fuga
```
