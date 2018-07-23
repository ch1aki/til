## CA証明書更新

CentOS6サーバのCA証明書が古くなっていたので更新した。

```
$ openssl x509 -in /etc/pki/tls/cert.pem -noout -dates
notBefore=Aug 17 22:00:00 2005 GMT
notAfter=Aug 17 22:00:00 2015 GMT # 2015年で切れている...
```

```
$ sudo rpm -qf /etc/pki/tls/certs/ca-bundle.crt
ca-certificates-2015.2.4-65.0.1.el6_6.noarch
```

`ca-certificates`パッケージから入っているのか。

yumインストールして完了。

```bash
$ sudo yum -q -y install ca-certificates
$ openssl x509 -in /etc/pki/tls/cert.pem -noout -dates
notBefore=Oct 29 15:59:56 2008 GMT
notAfter=Jan  1 00:00:00 2030 GMT
```
