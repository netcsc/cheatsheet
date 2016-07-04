```bash
git checkout -B [branch name]
git commit -am "[comment]"
git push origin [branch name]
```

# change permission on file
```bash
git update-index --chmod=+x script.sh
```

# Alias

```
[alias]
  co = checkout
  ci = commit
  st = status
  br = branch
  hist = log --pretty=format:'%h %ad | %s%d [%an]' --graph --date=short
  type = cat-file -t
  dump = cat-file -p
```
