# kontena-heroku

Run a Kontena master in Heroku.

## Quickstart

```
bin/setup APP
bin/deploy APP [IMAGE=kontena/server]

kontena master login --name yourmaster --code INITIAL_ADMIN_CODE https://HEROKU_APP.herokuapp.com/
kontena master init-cloud
```

## Capping all collections

Keeping mongodb under mlab limits requires additional collection capping / adjusting:

https://github.com/kontena/kontena/issues/2663
https://github.com/kontena/kontena/issues/2563

Start `heroku run bin/kontena-console -a APP`

```
HostNodeStat.collection.client.command(
  convertToCapped: HostNodeStat.collection.name,
  capped: true,
  size: 10.megabytes
)
```

```
GridServiceDeploy.collection.client.command(
  convertToCapped: GridServiceDeploy.collection.name,
  capped: true,
  size: 10.megabytes
)
```

## Advanced options

```
# Run setup without arguments to see full usage
bin/setup
```

## Updating master / locking master version

```
bin/deploy APP kontena/server:x.x.x
```
