```bash
cat access_log|awk '{if (substr($5,9,7)=="2013:21") print $2}'|sort|uniq -c|sort -nr|head
```

# top 20 URLs from the last 5000 hits
```bash
tail -n 5000 access_log | awk '{print $9}'| cut -d"?" -f1 | sort | uniq -c | sort -rn | head -20 
```

# top 20 True-Client-IP from the last 5000 hits. If the value of the IP in the resulting list is "-" (dash), the request by-passed Akamai
```bash
tail -n 5000 prdweb*/access_log | awk '{print $2}' | sort | uniq -c | sort -rn | head -20
```

# top 20 AKAMAI IPs from the last 5000 hits
```bash
tail -n 5000 prdweb*/access_log | awk '{print $1}' | sort | uniq -c | sort -rn | head -20
```

# top 20 URLs requested from a certain ip from the last 5000 hits
IP=198.49.68.32; tail -n 5000 logs/prdweb*/access_log | grep $IP | awk '{print $13}' | sort | uniq -c | sort -rn | head -20
```bash
IP=50.116.43.185; tail -n 5000 prdweb*/access_log | awk -v ip=$IP ' $1 ~ ip {freq[$13]++} END {for (x in freq) {print freq[x], x}}' | sort -rn | head -20
```

# top 20 URLS requested from a certain ip, excluding POST data, from the last 5000 hits
```bash
IP=50.116.43.185; tail -n 5000 logs/prdweb*/access_log | grep $IP | awk -F "[ ?]" '{print $14}' | sort | uniq -c | sort -rn | head -20
IP=157.55.33.40; tail -n 5000 logs/prdweb*/access_log | awk -F"[ ?]" -v ip=$IP ' $1 ~ ip {freq[$14]++} END {for (x in freq) {print freq[x], x}}' | sort -rn | head -20
IP=198.49.68.32; zcat access_log.201306100430.gz | tail -n 5000 | grep $IP | awk -F "[ ?]" '{print $14}' | sort | uniq -c | sort -rn | head -20
```

# top 20 user agents from the last 5000 hits
```bash
tail -n 5000 prdweb*/access_log | cut -d\  -f14- | sort | uniq -c | sort -rn | head -20
```

# sum of data (in MB) transferred in the last 5000 hits
```bash
tail -n 5000 prdweb*/* | awk '{sum+=$7} END {print sum/1048576}'
```

# list traffic by IP address at time e.g 2013, 1pm
```bash
cat access_log*|awk '{if (substr($5,9,7)=="2013:13") print $1 " " $2}'|sort|uniq -c|sort -nr|head
```

# list normal bot traffic by hours
```bash
cat access_log*|grep -i "mcafee\|bot\|spider\|crawler"|awk '{print $5}'|cut -f2 -d":"|sort|uniq -c
```

# list normal bot traffic at specified time, for example 8pm 2013
```bash
awk '{time=substr($5,9,7);if(time=="2013:12") print $0}' access_log*|cut -f 14- -d " "|grep -i "bot\|spider\|crawler"|sort|uniq -c|sort -nr|more
```
#user agent
```bash
grep -i bot access_log* | grep "10/Oct/2013:12" | cut -d"\"" -f6 | sort | uniq -c | sort -nr  | head -n 20
```

# by error
```bash
grep "\" 404 " access_log.20130926* | grep "26/Sep/2013:05" | awk '{print $2}' | sort | uniq -c | sort -nr  | head -n 20
grep "26/Aug/2013:11" access_log.201308260000* | grep "\" 404 " | awk '{print substr($9,1,20)}' | sort | uniq -c | sort -nr | head -n 20
awk -F"errorcode" '{ print $2 }' ordererrors.20140303-121600.txt | awk -F"}]" '{ print $1}' | grep "1605\|903"| sort | uniq -c | sort -rn
```
