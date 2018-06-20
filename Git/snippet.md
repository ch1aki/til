# よく使うコマンド

## 空コミット

```bash
git commit --allow-empty -m "first commit"
```

## マージ済みブランチを掃除する

```bash
git branch --merged | grep -v '*' | xargs git branch -d
```
