# Monitoring and usage reporting

## Usage reporting

```mermaid
flowchart LR
    N["NGINX gateway access logs"] --> T["Tagged log sources"]
    T --> G["Graylog"]
    G --> P["Domain and content-path classification"]
    P --> A["Usage aggregation"]
    A --> R["Customer usage reports"]
    R --> M["Monthly Telegram reports"]
```

Access logs from delivery gateways are forwarded with tags. Graylog pipelines and groupings classify data by domain and URL subdirectory to produce reports containing viewer-related metrics and transferred data volumes (GB or TB).

These reports support customer charging decisions; the reporting system does not itself perform billing or payment processing. The viewer identity method, handling of repeated requests and byte-counting accuracy have not been independently validated. No claim of exact unique-viewer counts is made.

## Monitoring

Zabbix monitors physical servers, availability, CPU, memory, disk, network utilization, physical link status, services and URLs. Telegram delivers operational alerts.

```mermaid
flowchart LR
    I["Infrastructure and service checks"] --> Z["Zabbix"]
    Z --> A["Alert conditions"]
    A --> T["Telegram notifications"]
```

Actual customer logs, addresses, access tokens, notification destinations and operational thresholds are intentionally excluded.
