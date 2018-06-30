## goxz,ghrでシュッとリリースする

GithubのSettingsから`public_repo`Scopeがついたaccess tokenを発行して、`GITHUB_TOKEN`環境変数で定義しておく。

```bash
$ cd PATH/TO/GOPROJECT

$ goxz -pv=0.1.0 -os=darwin,linux -arch=amd64 -d=dist .
[goxz] Initializing...
[goxz] Resources to include: [LICENSE README.md]
[goxz] Package to build: [github.com/akichan22/c2go]
[goxz] Building github.com/akichan22/c2go for linux/amd64
[goxz] Building github.com/akichan22/c2go for darwin/amd64
[goxz] Archiving c2go_0.1.0_darwin_amd64.zip
[goxz] Artifact archived to dist/c2go_0.1.0_darwin_amd64.zip
[goxz] Archiving c2go_0.1.0_linux_amd64.tar.gz
[goxz] Artifact archived to dist/c2go_0.1.0_linux_amd64.tar.gz
[goxz] Success!

$ tree dist/
dist/
├── c2go_0.1.0_darwin_amd64.zip
└── c2go_0.1.0_linux_amd64.tar.gz

0 directories, 2 files

$ ghr v0.1.0 dist/
==> Create a new release
--> Uploading: c2go_0.1.0_darwin_amd64.zip
--> Uploading: c2go_0.1.0_linux_amd64.tar.gz
```
