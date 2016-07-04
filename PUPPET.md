# Certificate
```
puppet master --configprint ssldir
puppet agent --configprint ssldir
puppet ca list
puppet cert sign --all
```

## Module
```
puppet agent --configprint modulepath
```

## Validate
```
puppet parser validate cowsayings/manifests/cowsay.pp
```
