---
sidebar_position: 6
---

# 🌠 Metrics

Butane nodes can enable [Butane SDK telemetry](https://docs.Butane.network/main/core/telemetry.html)
to allow for observing and gathering insights about the Butane application.
Under the hood, it uses the [`go-metrics`](https://github.com/hashicorp/go-metrics) package
and the Prometheus client library to expose different [types of metrics](https://prometheus.io/docs/concepts/metric_types/)
like gauges and counters.

![My Image](images/Group.png)

For best practices on how to use different metrics types,
check this [blog article](https://blog.pvincent.io/2017/12/prometheus-blog-series-part-2-metric-types/).

Find below a list of supported Butane modules with custom metrics and telemetry.
Using the metrics you can e.g. run performance profiles
and display them in a [Grafana](https://grafana.com/) dashboard.
