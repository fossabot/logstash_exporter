# Logstash exporter [![Build Status](https://travis-ci.org/sequra/logstash_exporter.svg)]
[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bgithub.com%2Fsritoleti%2Flogstash_exporter.svg?type=shield)](https://app.fossa.io/projects/git%2Bgithub.com%2Fsritoleti%2Flogstash_exporter?ref=badge_shield)
Prometheus exporter for the metrics available in Logstash since version 5.0.

Continuous integration: [travis](https://travis-ci.org/sequra/logstash_exporter/)

## Usage

```bash
go get -u github.com/sequra/logstash_exporter
cd $GOPATH/src/github.com/sequra/logstash_exporter
make
./logstash_exporter --web.listen-address=:1234 --logstash.endpoint="http://localhost:1235"
```

### Flags

```sh
logstash_exporter --help
usage: logstash_exporter [<flags>]

Flags:
  -h, --help              Show context-sensitive help (also try --help-long and
                          --help-man).
      --logstash.endpoint="http://localhost:9600"
                          The protocol, host and port on which logstash metrics
                          API listens
      --web.listen-address=":9198"
                          Address on which to expose metrics and web interface.
      --log.level="info"  Only log messages with the given severity or above.
                          Valid levels: [debug, info, warn, error, fatal]
      --log.format="logger:stderr"
                          Set the log target and format. Example:
                          "logger:syslog?appname=bob&local=7" or
                          "logger:stdout?json=true"
      --version           Show application version.
```

## Implemented metrics

* `logstash_exporter_build_info` (gauge)
* `logstash_exporter_scrape_duration_seconds`: logstash_exporter: Duration of a scrape job. (summary)
* `logstash_info_jvm`: A metric with a constant '1' value labeled by name, version and vendor of the JVM running Logstash. (counter)
* `logstash_info_node`: A metric with a constant '1' value labeled by Logstash version. (counter)
* `logstash_info_os`: A metric with a constant '1' value labeled by name, arch, version and available_processors to the OS running Logstash. (counter)
* `logstash_node_gc_collection_duration_seconds_total` (counter)
* `logstash_node_gc_collection_total` (gauge)
* `logstash_node_jvm_threads_count` (gauge)
* `logstash_node_jvm_threads_peak_count` (gauge)
* `logstash_node_mem_heap_committed_bytes` (gauge)
* `logstash_node_mem_heap_max_bytes` (gauge)
* `logstash_node_mem_heap_used_bytes` (gauge)
* `logstash_node_mem_nonheap_committed_bytes` (gauge)
* `logstash_node_mem_nonheap_used_bytes` (gauge)
* `logstash_node_mem_pool_committed_bytes` (gauge)
* `logstash_node_mem_pool_max_bytes` (gauge)
* `logstash_node_mem_pool_peak_max_bytes` (gauge)
* `logstash_node_mem_pool_peak_used_bytes` (gauge)
* `logstash_node_mem_pool_used_bytes` (gauge)
* `logstash_node_pipeline_duration_seconds_total` (counter)
* `logstash_node_pipeline_events_filtered_total` (counter)
* `logstash_node_pipeline_events_in_total` (counter)
* `logstash_node_pipeline_events_out_total` (counter)
* `logstash_node_pipeline_queue_push_duration_seconds_total` (counter)
* `logstash_node_plugin_bulk_requests_failures_total` (counter)
* `logstash_node_plugin_bulk_requests_successes_total` (counter)
* `logstash_node_plugin_bulk_requests_with_errors_total` (counter)
* `logstash_node_plugin_documents_failures_total` (counter)
* `logstash_node_plugin_documents_successes_total` (counter)
* `logstash_node_plugin_duration_seconds_total` (counter
* `logstash_node_plugin_queue_push_duration_seconds_total` (counter)
* `logstash_node_plugin_events_in_total` (counter)
* `logstash_node_plugin_events_out_total` (counter)
* `logstash_node_plugin_current_connections_count` (gauge)
* `logstash_node_plugin_peak_connections_count` (gauge)
* `logstash_node_process_cpu_total_seconds_total` (counter)
* `logstash_node_process_max_filedescriptors` (gauge)
* `logstash_node_process_mem_total_virtual_bytes` (gauge)
* `logstash_node_process_open_filedescriptors` (gauge)
* `logstash_node_queue_events` (counter)
* `logstash_node_queue_size_bytes` (counter)
* `logstash_node_queue_max_size_bytes` (counter)
* `logstash_node_queue_max_unread_events`: queue_max_ (counter)
* `logstash_node_queue_page_capacity_bytes`: queue_page_capacity_bytes (counter)
* `logstash_node_up`: whether logstash node is up (1) or not (0) (gauge)

## Integration tests
In order to execute manual integration tests (to know if certain logstash version is compatible with logstash-exporter), you can follow instructions present on file [integration-tests/README.md](integration-tests/README.md).


## License
[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bgithub.com%2Fsritoleti%2Flogstash_exporter.svg?type=large)](https://app.fossa.io/projects/git%2Bgithub.com%2Fsritoleti%2Flogstash_exporter?ref=badge_large)