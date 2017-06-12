# kontena-heroku

Run a Kontena master in Heroku.

```
bin/setup APP IMAGE

kontena master login --name yourmaster --code INITIAL_ADMIN_CODE https://HEROKU_APP.herokuapp.com/
kontena master init-cloud

```

## Building your own

git clone git@github.com:kontena/kontena
cd kontena/server
docker build -t mattipaksula/kontena-server:1.3.0 .
docker push mattipaksula/kontena-server:1.3.0

## Tagging your own

(note https://github.com/kontena/kontena/pull/2455)
```
docker pull kontena/server:1.3.0
docker tag kontena/server:1.3.0 mattipaksula/kontena-server:1.3.0
docker push mattipaksula/kontena-server:1.3.0
```
