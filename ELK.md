### Health Check
```
http://localhost:9200/_cluster/health?pretty=true
```

### Shard Status
```
http://localhost:9200/_cat/shards
```

### docker/logstash
```
docker run -d -v "$PWD":/config-dir -v /var/log/:/var/log --name logstash logstash logstash -f /config-dir/logstash-shipper.conf
```

### logstash-shipper.conf
```
input {
  file {
    path => [ "/var/log/*.log", "/var/log/messages", "/var/log/syslog" ]
    type => "syslog"
  }
}

output {
  stdout { codec => rubydebug }
  redis { host => "l27.0.0.1" data_type => "list" key => "logstash" }
}
```
