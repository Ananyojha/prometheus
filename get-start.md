[Monitor nginx using Prometheus](https://antonputra.com/monitoring/monitor-nginx-with-prometheus/#install-nginx-prometheus-exporter)

Prometheus is a powerful open-source monitoring and alerting tool that is used to collect and store time-series data. By default, Prometheus stores its time-series database in a directory named `./data`. This location is determined by the `--storage.tsdb.path` flag when starting Prometheus.

Here's a breakdown of what this means:

1. **Time-Series Database (TSDB)**: Prometheus uses a time-series database to store all the collected metrics data. A time-series database is optimized for handling time-stamped data points associated with a particular metric over time.

2. **`./data` Directory**: The `./data` directory is a relative path to the current working directory where Prometheus is started. When you start Prometheus without specifying a custom storage path, it will create a directory named `data` in the current working directory to store its time-series database.

3. **Flag `--storage.tsdb.path`**: This flag is used to set a custom path for the time-series database. If you want to store the database in a different location, you can provide this flag with the desired path when starting Prometheus. For example:

   ```bash
   prometheus --storage.tsdb.path=/path/to/custom/directory
   ```

   In this case, Prometheus will create and use the `/path/to/custom/directory` to store its time-series database.

The time-series database is where Prometheus stores all the metrics data collected from various targets (e.g., Nginx, system metrics, custom application metrics, etc.). It uses a combination of efficient data structures and compression techniques to optimize storage and retrieval of time-series data.

Keep in mind that the Prometheus data directory can grow significantly depending on the number of metrics being collected and the retention period configured. It's essential to monitor disk usage to prevent the database from using up too much disk space.

Additionally, Prometheus offers various configuration options related to storage, such as retention periods, compaction settings, and more. These settings are defined in the `prometheus.yml` configuration file under the `storage` section.

For further details on Prometheus storage configuration and best practices, refer to the official Prometheus documentation: https://prometheus.io/docs/prometheus/latest/storage/
