# Local Otel Collector

All simulations are via local Go service, including
- target probe (http://localhost:8080/netprobe-target )
- /health scrape endpoint (http://localhost:8080/health)
- metrics receiver OBS platform (http://localhost:8080/export)

## Documentations

Run Otel collector: https://opentelemetry.io/docs/collector/installation/

Configure Otel collector: https://opentelemetry.io/docs/collector/configuration/#receivers

Run bb exporter: https://prometheus.io/docs/guides/multi-target-exporter/

- blackbox.yml errors: https://github.com/prometheus/blackbox_exporter/issues/1295

### Run Otel + bb exporter

```
docker \
  run -p 9090:9090 \
  --mount type=bind,source="$(pwd)"/prometheus.yml,target=/prometheus.yml,readonly \
  prom/prometheus \
  --config.file="/prometheus.yml"
```

