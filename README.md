# Overview

https://github.com/confluentinc/jmx-monitoring-stacks provides example JMX monitoring stacks that can monitor Confluent Platform.
While Confluent Control Center provides an opinionated view of Apache Kafka monitoring, JMX monitoring stacks serve a larger purpose to our users, allowing them to setup monitoring across multiple parts of their organization, many outside of Kafka, and to have a single pane of glass.

* [jmxexporter-prometheus-grafana](jmxexporter-prometheus-grafana)
* [jolokia-elastic-kibana](jolokia-elastic-kibana)

# Disclaimer

This repo is intentionally private at the moment.

# Run

This repo is intended to be run specifically with [cp-demo](https://github.com/confluentinc/cp-demo).

1. Define parameters:

* `CONFLUENT_RELEASE_TAG_OR_BRANCH`: GitHub branch to use in both confluentinc/cp-demo and confluentinc/jmx-monitoring-stacks (supports only `5.5.0-post` at this time)
* `STACK`: monitoring stack to demo (supports either [jmxexporter-prometheus-grafana](jmxexporter-prometheus-grafana) or [jolokia-elastic-kibana](jolokia-elastic-kibana))

```bash
CONFLUENT_RELEASE_TAG_OR_BRANCH=5.5.0-post
STACK=jmxexporter-prometheus-grafana
```

2. Clone cp-demo and checkout the appropriate release.

```bash
[[ -d "cp-demo" ]] || git clone https://github.com/confluentinc/cp-demo.git
(cd cp-demo && git fetch && git checkout ${CONFLUENT_RELEASE_TAG_OR_BRANCH} && git pull)
```

3. Clone this repo `jmx-monitoring-stacks` and checkout a compatible release.

```bash
[[ -d "jmx-monitoring-stacks" ]] || git clone https://github.com/confluentinc/jmx-monitoring-stacks.git
(cd jmx-monitoring-stacks && git fetch && git checkout ${CONFLUENT_RELEASE_TAG_OR_BRANCH} && git pull)
```

4. Start cp-demo with the STACK selected.

```bash
${STACK}/start.sh
```

5. Stop cp-demo and the STACK.

```bash
${STACK}/stop.sh
```