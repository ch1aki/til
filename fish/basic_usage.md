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

###  $PATHの設定

`~/.config/fish/config.fish`に設定する方法。

```
set PATH /usr/local/bin /usr/sbin $PATH
```

または、ユニバーサルな変数に設定する方法。(これは設定ファイルに書いてはならない...)

```
set -U fish_user_paths /usr/local/bin $fish_user_paths
```
