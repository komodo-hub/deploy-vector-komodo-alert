# Deploy Vector Komodo Alert

Part of the [*Komodo Hub* collection.](https://github.com/komodo-hub/komodo-hub)

Runs Vector as an [http server](https://vector.dev/docs/reference/configuration/sources/http_server/), which acts as a custom Komodo Alerter endpoint, and routes the Alerts to Grafana Loki.

https://hub.docker.com/r/timberio/vector

## Komodo Resource TOML

```toml
[[stack]]
name = "vector_komodo_alert"
[stack.config]
repo = "komodo-hub/deploy-vector-komodo-alert"
environment = """
  # https://hub.docker.com/r/timberio/vector
  VECTOR_TAG = latest-debian
  # https://docs.docker.com/engine/logging/configure
  LOGGING_DRIVER = local
  # Vector will listen on this address for incoming alerts from Komodo
  SERVER_ADDRESS = "0.0.0.0:7000"
  # Route alerts to Loki
  LOKI_ENDPOINT = http://loki:3100
"""
```