# lxd-image-opentsdb
###### Image with OpenTSDB for use with lxc/lxd

## Import
* Download [opentsdb.tar.gz](https://github.com/cryptofuture/lxd-image-opentsdb/raw/master/opentsdb.tar.gz)
* Check sha256sum with `sha256sum opentsdb.tar.gz`

```bash
# Correct output:
31435f78524a0e585d952b391295e94c07e775d6de9803b54cc1676a9f94c19d  opentsdb.tar.gz
```

* Import image with: `lxc image import opentsdb.tar.gz --alias opentsdb`

## Create container from image
* Run `lxc launch opentsdb containernameyouwish`

## About image and installed software
Image based on [xenial-light](https://github.com/cryptofuture/lxd-image-xenial-light/) image
* Installed and configured [Apache HBase](https://hbase.apache.org/) in standalone mode, from [ppa:hda-me/hbase](https://launchpad.net/~hda-me/+archive/ubuntu/hbase)
* [OpenTSDB](https://github.com/OpenTSDB/opentsdb) package installed from from [releases page](https://github.com/OpenTSDB/opentsdb/releases)
* [Grafana](http://grafana.org/) installed from [apt repository](http://docs.grafana.org/installation/debian/) and opentsdb configured as [Data Source](http://docs.grafana.org/datasources/opentsdb/)

## Updates
`unattended-upgrades` configured for auto updates when applicable.  
Basically all you may need to update manually will be OpenTSDB, since there no repository or PPA available yet.  
Use deb package from [releases page](https://github.com/OpenTSDB/opentsdb/releases).

## Testing/using it with [netdata](https://github.com/firehol/netdata)
Add `opentsdb` to `/etc/hosts`, like: `127.0.0.1	localhost opentsdb`
Add `tsd.core.auto_create_metrics = true` to OpenTSDB config
