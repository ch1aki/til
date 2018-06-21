## /etc/nsswitch.conf

> ネームサービスのスイッチの設定ファイル。
> 
> ネームサービススイッチ (Name Service Switch; NSS) の設定ファイル /etc/nsswitch.conf は、 GNU C ライブラリが いろいろなカテゴリーの名前サービス情報を、どの情報源から どの順序で取得するかを判断するのに使用される (情報の各カテゴリーはデータベース名で識別される)。
> 設定ファイルは通常の ASCII テキストで、列はスペースかタブ文字で 区切られる。最初の列はデータベース名を示す。 残りの列は、情報を問い合わせる情報源の順序と、 検索結果に対して実行するアクションを規定する。

例:

```
passwd:
compat

group:
compat

shadow:
compat

hosts:
dns [!UNAVAIL=return] files

networks:
nis [NOTFOUND=return] files

ethers:
nis [NOTFOUND=return] files

protocols:
nis [NOTFOUND=return] files

rpc:
nis [NOTFOUND=return] files

services:
nis [NOTFOUND=return] files
```

結果が得られるまで、書かれている順に検索を行う。

例えば、LDAP環境ならつぎのような感じになる。

```bash
$ grep -e ^passwd -e ^shadow -e ^group /etc/nsswitch.conf
passwd:     files ldap
shadow:     files ldap
group:      files ldap

```
