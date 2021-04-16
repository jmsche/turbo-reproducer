Turbo Mercure Reproducer
========================

Token does not seem to be passed to the Mercure request, hence a 401 error.

dunglas/mercure image used for this reproducer is v0.10.4 as I can't manage to set CORS policy on v0.11.

Also for some reason HTTPS forward from Docker does not seem to work, no idea why.

I think the issue is not related to Symfony CLI as the XHR call is made on the correct forwarded
HTTP port (3010), not the one from Symfony CLI.

Launch reproducer
-----------------

```bash
git clone https://github.com/jmsche/turbo-reproducer.git
composer install
yarn install
yarn run dev
docker-compose up -d
symfony serve -d
```

Then check the default page (eg. https://127.0.0.1:8000/), open the network tab from your browser console
& reload the page: XHR call does not seem to carry the `Authorization` header.

Stop reproducer
---------------

```bash
symfony server:stop
docker-compose stop
```
