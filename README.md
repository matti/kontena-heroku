# kontena-heroku

Run a Kontena master in Heroku.

## Quickstart

```
bin/setup APP
bin/deploy APP

kontena master login --name yourmaster --code INITIAL_ADMIN_CODE https://HEROKU_APP.herokuapp.com/

#maybe:
kontena master init-cloud
```

## Capping all collections

Keeping mongodb under mlab limits requires additional collection capping / adjusting:

https://github.com/kontena/kontena/issues/2663

Start `heroku run bin/kontena-console -a APP`

```
HostNodeStat.collection.client.command(
  convertToCapped: HostNodeStat.collection.name,
  capped: true,
  size: 10.megabytes
)
```

Additionally you need to `repairDatabase` to compact the size every now and then:

```
heroku addons:create scheduler:standard --wait -a APP
heroku addons:open scheduler -a APP
```

And create a task with:

```
ruby -r ./app/boot.rb -e "puts Mongoid.default_client.command(repairDatabase: 1).documents.inspect"
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
