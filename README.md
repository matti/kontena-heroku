# kontena-heroku

Run a Kontena master in Heroku.

## Quickstart

```
bin/setup APP
bin/deploy APP [IMAGE=kontena/server]

kontena master login --name yourmaster --code INITIAL_ADMIN_CODE https://HEROKU_APP.herokuapp.com/
kontena master init-cloud
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
