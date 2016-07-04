# Generate Javacore
## Get PID
```
watch "ps -eo pcpu,pid,user,args | sort -k 1 -r | head -6" 
```
or
```
cat /opt/WebSphere/AppServer/profiles/AppSrv01/logs/WC_stgmall1/WC_stgmall1.pid
```
## Genearte javacore  
```
kill -3 PID
```
# grep a string out of files printing only the file name
```bash
grep -H "<ErrorMessage>" SystemOut*.log -R | cut -d: -f1
```

# Check global file write permission security
```
for PART in `awk '(!/^#/ && $6 != "0") { print $2 }' /etc/fstab 2>/dev/null`; do find $PART -xdev -type f \( -perm -0002 -a ! -perm -1000 \) -print 2>/dev/null; done
```

# check large file
```
find . -type f -size +50000k -exec ls -lh {} \; | awk '{ print $9 ": " $5 }'
```

# extension
## change from one to another
```
for f in *.php4; do mv $f `basename $f .php4`.php; done;
```
# add
```
for f in *; do mv $f `basename $f `.txt; done;
```
# remove
```
for f in *.txt; do mv $f `basename $f .txt`; done;
```
#  AIX 
```
tar -cvf - /some/directory/path/ | gzip -c | split -b 500m - file.tgz.
```
# fine and sort
```
find -type f -print0 | xargs -r0 stat -c %y\ %n | sort
```
# find file newer than another file and cp
```
find . -name "*.xml" -newer SKU_1408619449286_557746.xml -exec cp {} /data/full_local/ \;
```
# find archive and list files
```
find . -name "daily_archive.20140*.gz" -exec tar ztvf {} \; > /tmp/find.log
```

# Check RHEL release
```
cat /etc/redhat-release
```

# Run Level
```
chkconfig –-list | grep 5:on
chkconfig <Service-Name> on –level 3
```

# Kernel parameters
```
/etc/sysctl.conf
sysctl -p
```

# NFS
## server
```
yum install nfs-utils nfs-utils-lib
chkconfig nfs on 
service rpcbind start
service nfs start
vi /etc/exports   # add /home 12.33.44.555(rw,sync,no_root_squash,no_subtree_check)
exportfs -a
```
## client
```
yum install nfs-utils nfs-utils-lib
mkdir -p /mnt/nfs/home
mount 12.34.56.789:/home /mnt/nfs/home
df -h # validate or use mount
```

## alais
```
alias ll='ls -al'
```

## Allocate additional disk
```
mkfs -t ext4 /dev/xvdc
echo "/dev/xvdc /mount_name ext4 defaults 0 0" >> /etc/fstab
mkdir -p /mount_name
mount /mount_name
```
