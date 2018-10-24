# Wavefront BOSH Release for Telegraf

### Release deployment properties

`telegraf.tags`: a hash of name/value tags to apply to all metrics  
`telegraf.interval`: the collection interval (default: 60s)  
`telegraf.host_prefix`: A prefix to add to the hostname for metrics that do not specify one  
`telegraf.plugin_config`: Complete configuration for telegraf plugins to be used  
`telegraf.wavefront.host`: DNS name or IP of Wavefront Proxy  
`telegraf.wavefront.port`: Port number for Wavefront Proxy (default: 2878)  
`telegraf.wavefront.prefix`: Prefix to add to all metric names  


### Build BOSH Release
First add the Telegraf binary blog.  Tested with 1.8.2, should work with newer versions as well.

```
wget https://dl.influxdata.com/telegraf/releases/telegraf-1.8.2_linux_amd64.tar.gz
bosh add-blob telegraf-1.8.2_linux_amd64.tar.gz telegraf/telegraf-1.8.2_linux_amd64.tar.gz
```

Next create and upload the BOSH release.  (use --force option if required)

```
bosh create-release
bosh -e <bosh_director> upload-release
```

The release is now ready for deployment.