# Grafana on Heroku

> ...by using Docker

## Refresh Dockerfile

Run `./dockerfile-assemble.sh`. It will update the local copy of the recommended Dockerfile for customization, then merge it with the necessary bits to make it work on Heroku.

## Clean instance

Run `./reset.sh`. It will reset the database, then restart the web dyno.

## Build & Deploy for Heroku

### Pull new version of Grafana
docker pull grafana/grafana

## Upgrading & Deploying on Heroku:

1. `docker pull grafana/grafana`
2. `./dockerfile-update.sh`
3. `heroku auth:token | docker login --username=_ registry.heroku.com --password-stdin`
4. Necessary for Apple ARM: `docker buildx build --platform linux/amd64 -t grafana-heroku .`
5. Check `docker images` for <TAGID>: `docker tag <TAGID> registry.heroku.com/yeast-grafana/web`
6. `docker push registry.heroku.com/yeast-grafana/web`
7. `heroku container:push web`
8. `heroku container:release web`

