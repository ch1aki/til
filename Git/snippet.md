# よく使うコマンド

## 空コミット

```bash
git commit --allow-empty -m "first commit"
```

## マージ済みブランチを掃除する

```bash
git branch --merged | grep -v '*' | xargs git branch -d
```

## リモートブランチを手元にチェックアウトする

```bash
git checkout -b <local-branch-name> origin/<remote-branch-name>
```

## fork元リポジトリに追従する

```bash
g checkout master

# fork元を'upstream'としてremoteに追加
git remote add upstream git@github.com:foo/bar

# upstreamをfetch
git fetch upstream

# forkしたリポジトリのmasterにfork元のmasterをmerge
git merge upstream/master
```

example:

```bash
➜  kanmon git:(master) g remote add upstream git@github.com:buty4649/kanmon.git
➜  kanmon git:(master) g fetch upstream
remote: Counting objects: 1, done.
remote: Total 1 (delta 0), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (1/1), done.
From github.com:buty4649/kanmon
 * [new branch]      master     -> upstream/master
➜  kanmon git:(master) g branch -a
  catch_already_opened_exception
* master
  remotes/origin/HEAD -> origin/master
  remotes/origin/catch_already_opened_exception
  remotes/origin/master
  remotes/upstream/master
➜  kanmon git:(master) g merge upstream/master
Updating 468a060..a785ec7
Fast-forward
 lib/kanmon/cli.rb | 3 +++
 1 file changed, 3 insertions(+)

```
