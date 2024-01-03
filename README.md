
# Clickhouse Zeek Logs Integration

This is how I pushed zeek logs to clickhouse.

# Setup

- Install Zeek on a machine [(Installation)](https://software.opensuse.org//download.html?project=security:zeek&package=zeek)
- Install Fluent Bit on the same machine [(Installation)](https://docs.fluentbit.io/manual/installation/getting-started-with-fluent-bit)
- Install clickhouse on an another machine [(Installation)](https://clickhouse.com/docs/en/install)
## Create Clickhouse Tables
Use the `tables.sql` file in the repo to create the tables in clickhouse like this
```bash
clickhouse client --multiquery < tables.sql
```
## Zeek Logs in JSON format
Go to `/opt/zeek/share/zeek/site/local.zeek` and add line
```zeek
@load policy/tuning/json-logs.zeek
```
## Fluent Bit Configuration
Copy and paste the content of `fluent-bit` folder to `/etc/fluent-bit` and restart the service. Make sure the path to the logs is correct and the clickhouse server configuration is setup correctly in the files, as well as the `script.lua`.


