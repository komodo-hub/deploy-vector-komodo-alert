# Deploy Vector Komodo Alert

Runs Vector as an [http server](https://vector.dev/docs/reference/configuration/sources/http_server/), which acts as a custom Komodo Alerter endpoint, and routes the Alerts to Grafana Loki.

## Komodo Resource TOML

```toml
[[stack]]
name = "vector_komodo_alert"
[stack.config]
repo = "mbecker20/deploy_vector_komodo_alert"
environment = """
	# https://hub.docker.com/r/timberio/vector
	VECTOR_TAG=latest-distroless
	LOGGING_DRIVER=local

	# Vector will listen on this address for incoming alerts from Komodo
	SERVER_ADDRESS="0.0.0.0:7000"
	# Route alerts to Loki
	LOKI_ENDPOINT=http://loki:3100
"""
```