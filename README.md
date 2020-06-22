# prometheus-docker

Local repo for prometheus and pushgateway to run locally

This demonstrate to run prometheus and pushgateway to  run locally using docker compose and docker swarm

![Prometheus Architecture](https://prometheus.io/assets/architecture.png)
*Image from prometheus official website*

Following components are included:

* prometheus
* cadvisor
* node-exporter
* collectd
* alertmanager : Slack webhook url is used for alerts.
* pushgateway
* alerta

## Pre-Requisite

This requires installation of [docker-for-desktop](https://www.docker.com/products/docker-desktop)

## References

* <https://medium.com/skedler/monitoring-servers-and-docker-containers-using-prometheus-with-grafana-87cf961fe1e0>
* <https://github.com/vegasbrianc/prometheus>

## Docker Compose

In order to run this simply download the folder and run it using following commands:

```bash
# Run it from the parent directory i.e. path where docker-compose.yml file exists
~/prometheus-docker$docker-compose up [-d]
```

 *Use -d to run docker-compose in detach mode.*

To stop/bring down the container run following command:

```bash
~/prometheus-docker$docker-compose down --remove-orphans
```

*Use --remove-orphans to remove the containers for services not defined in the Compose file.*

## Docker Stack Deploy

To deploy using docker staxck, run the below command:

```bash
docker stack deploy --compose-file docker-stack.yml prom_stack
```

To remove the deploymnet, run the following command:

```bash
docker stack remove prom_stack
```

## Open Issue

Prometheus unable to scrape cadvisor in docker stack/k8s:  <https://github.com/gos-apoorv/prometheus-docker/issues/1>
