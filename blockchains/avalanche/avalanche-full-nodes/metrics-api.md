# Metrics API

## Metrics API

The API allows clients to get statistics about a node’s health and performance.

### Endpoint <a href="endpoint" id="endpoint"></a>

```
/ext/metrics
```

### Usage <a href="usage" id="usage"></a>

To get the node metrics:

```bash
//Request
curl -X POST http:///<your-node-id>.ankr.com/ext/metrics
```

### Format <a href="format" id="format"></a>

This API produces Prometheus compatible metrics. See [here](https://github.com/prometheus/docs/blob/master/content/docs/instrumenting/exposition\_formats.md) for information on Prometheus’ formatting.[PreviousHealth API](health-api.md)[NextAdmin API](admin-api.md)

![](https://lh4.googleusercontent.com/-RiWbCRl5SW0/AAAAAAAAAAI/AAAAAAAAAAA/AMZuucmjUmtj3nXiWaxdDtE4WVrLmNYrsg/photo.jpg)

Last updated 11 months ago
