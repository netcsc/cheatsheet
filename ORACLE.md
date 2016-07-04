
```sql
select * from v$resource_limit where resource_name in ('processes', 'sessions', 'transactions');
select count(1) from v$process;
alter system set PROCESSES=2000 scope = spfile;
alter system set db_files=2000 scope=spfile;
shutdown immediate;
show pdbs;
```

```
#!/bin/bash

cat >  lspdb.sh <<EOL
sqlplus <<LABEL
sys/oracle as sysdba
show pdbs;
exit
LABEL
EOL

chmod +x lspdb.sh
./lspdb.sh

touch mountdb.sh
chmod +x mountdb.sh
echo "sqlplus <<LABEL" > mountdb.sh
echo "sys/oracle as sysdba" >> mountdb.sh

for db in $(./lspdb.sh | grep "_PDB_" | awk '{print $2}' | sort -u); do
  echo "alter pluggable database ${db} open read write;" >> mountdb.sh
done

echo "exit" >> mountdb.sh
echo "LABEL" >> mountdb.sh


./mountdb.sh
./lspdb.sh
```
