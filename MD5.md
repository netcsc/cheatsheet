# Hashing files
```
md5sum file.gz > md5sums.md5
md5sum -c md5sums.md5
```

# Recurisvely hashing files
```
find dir_folder -type f -print0 | xargs -0 md5sum >> checksum.md5
```
