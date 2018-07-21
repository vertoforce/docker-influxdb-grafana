# About
Docker compose for influxdb and grafana stack


## Deployment

Get the stack (only once):
```
docker-compose pull
```

Run
```
docker-compose up
# Setup correct permissions
chmod -R 777 grafana_data influxdb_data
# Run again
docker-compose up
```

Stop:
```
docker-compose stop
docker-compose rm
```


## Usage

### Add influx db

In Grafana:

```
Type: influxDB
URL: http://influxdb:8086
```


### Collectd clients

For all collectd clients sending data to this stack, modify
`/etc/collectd/collectd.conf` and add the following lines:

Make sure to set the appropriate ip.
Note that it uses udp so make sure all firewall rules and such are udp

```
LoadPlugin network
<Plugin network>
    Server "127.0.0.1" "25826"
</Plugin>
```


### Login

Default grafana login:

http://localhost:3000/login
```
admin/admin
```

