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
