# Grafana on Heroku

### Pull new version of Grafana
docker pull grafana/grafana

## Upgrading & Deploying on Heroku:

1. `docker pull grafana/grafana`
2. `export DOCKER_DEFAULT_PLATFORM=linux/amd64`
3. `heroku container:push web -a yeast-grafana`
4. `heroku container:release web -a yeast-grafana`

