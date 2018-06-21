# hiera

## 基本的な動作

`/etc/puppet/hiera.yaml`ファイルを読み込む。

```yaml
---
:backends:
  - yaml
:yaml:
  :datadir: /etc/puppet/hieradata
:hierarchy:
  - hosts/%{::hostname}-%{::env}
  - hosts/%{::hostname}
  - roles/%{myrole}
  - common
```

* `:datadir:`が読み込むhieradataのパス

* `:hierarchy:`が読み込むhieraのリスト。*上から順番に読み込む。*

### 例

あるwebサーバで環境によって次のような設定を行わせたいとする。

* production環境

    * `document_root`を`/opt`にしたい

* test環境

    * `document_root`を`/opt`にしたい

    * `thread_num`をデフォルト値から`10`にしたい

これをhieraで実現するなら、hiera.yamlで定義されている順(`hosts/%{::hostname}-%{::env}`, `hosts/%{::hostname}`, `roles/%{myrole}`, `common`)で値が検索されるので、
次のように`<hostname>-test.yaml`に設定を追加するだけで良い。`document_root`は`<hostname>.yaml`で定義されているので、新たにtestの方で定義する必要はない。

* `hieradata/hosts/<hostname>-test.yaml`

    ```yaml
    apatch::param::thread_num: 10
    ```

* `hieradata/hosts/<hostname>.yaml`

    ```yaml
    apatch::param::document_root: /opt
    ```

