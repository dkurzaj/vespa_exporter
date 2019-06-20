## Exporting Vespa metrics to Prometheus

Specify vespa-configserver (hostname:port) in environment VESPA_CONFIGSERVER

Usage with docker

    # docker build -t vespa-exporter .
    # docker run -e VESPA_CONFIGSERVER=vespa-configserver.example.com:19071 vespa-exporter

### Filter the exposed metrics

If you want to only expose the metrics you want (to limit the amount of data exported to the Prometheus server for example), you can specify a whitelist in a separate file. A simple text file a containing a metric name per line. The name of the metric must be expressed as it is sent to the exporter (with `_` between words). You then have to specify the name of this file in environment VESPA_METRICS_WHITELIST_FILE.

Here is an example of three metrics in the whitelist file:
```
vespa_distributor_vds_idealstate_set_bucket_state_pending
vespa_searchnode_status_code_up
vespa_searchnode_content_proton_resource_usage_disk
```
