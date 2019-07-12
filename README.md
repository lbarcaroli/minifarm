Minifarm
========

A minimal experiment to build a local dev farm environment.

Prerequisites
-------------

Use `mkcert` to generate your own (local!) valid TLS CA.

```shell
go get -u github.com/FiloSottile/mkcert
sudo mkcert -install
cd ssl-certs
mkcert jenkins.dev
mkcert nexus.dev
```

Add this entries to your `127.0.0.1` line in `/etc/hosts`:

```
sudo sed 's/127.0.0.1.*/& nexus.dev jenkins.dev/' /etc/hosts
```

(or do it by hand with your favourite editor).
You also need a working `docker-compose`.


Run
---

```
docker-compose up -d && docker-compose logs -f
```

Play
----

Open a browser at `nexus.dev` and `jenkins.dev`.
