StatsD + Graphite + Grafana 4
---------------------------------------------

This image contains a sensible default configuration of StatsD, Graphite and Grafana

### Running the Image ###

This image is published in [Docker Hub](https://hub.docker.com/r/eminn/grafana-dashboard) and all you
need as a prerequisite is having `docker`, `docker-compose`, and `make` installed on your machine. The container exposes the following ports:

- `80`: the Grafana web interface.
- `81`: the Graphite web port
- `2003`: the Graphite data port
- `2004`: the Graphite pickle protocol port
- `8125`: the StatsD port.
- `8126`: the StatsD administrative port.

To start a container with this image you just need to run the following command:

```bash
$ make up
```

To stop the container
```bash
$ make down
```

To run container's shell
```bash
$ make shell
```

To view the container log
```bash
$ make tail
```

If you already have services running on your host that are using any of these ports, you may wish to map the container
ports to whatever you want by changing left side number in the `--publish` parameters. You can omit ports you do not plan to use. Find more details about mapping ports in the Docker documentation on [Binding container ports to the host](https://docs.docker.com/engine/userguide/networking/default_network/binding/) and [Legacy container links](https://docs.docker.com/engine/userguide/networking/default_network/dockerlinks/).




### Using the Dashboards ###

Once your container is running all you need to do is:

- open your browser pointing to http://localhost:80 (or another port if you changed it)
  - Docker with VirtualBox on macOS: use `docker-machine ip` instead of `localhost`
- login with the default username (admin) and password (admin)
- open existing dashboard (or create a new one) and select 'Local Graphite' datasource
- play with the dashboard at your wish...


### Persisted Data ###

When running `make up`, directories are created on your host and mounted into the Docker container, allowing graphite and grafana to persist data and settings between runs of the container.

