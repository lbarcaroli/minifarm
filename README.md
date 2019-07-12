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
sudo sed -i 's/127\.0\.0\.1.*/& nexus.dev jenkins.dev/' /etc/hosts
```

(or do it by hand with your favourite editor).
You also need a working `docker-compose`.


Run
---


Start the lab:

```
docker-compose up -d && docker-compose logs -f
```

Play
----

Open a browser at `nexus.dev` and `jenkins.dev`.

The first time you reach jenkins, you will need to do a boot up configuration.
You will need to retrieve a password from the container:

```
docker-compose exec jenkins cat /var/jenkins_home/secrets/initialAdminPassword
```

Then proceed to install the plugins at your choice and go on.
