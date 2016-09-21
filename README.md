[![](https://images.microbadger.com/badges/version/mihailbinev/nginx.svg)](https://microbadger.com/images/mihailbinev/nginx "Get your own version badge on microbadger.com")

mihailbinev/nginx
=================

* nginx
* Supervisor

The nginx is started and monitored by Supervisor.

To pull the image

```sh
docker pull mihailbinev/nginx
```

If you want to build the image

```sh
docker build -t mihailbinev/nginx .
```

To run it

```sh
docker run --rm -it -v /path/to/project:/var/www/project -p 80:80 mihailbinev/nginx
```

With docker-compose
-------------------

With [https://docs.docker.com/compose/install/](docker-compose) everything is a bit bearable.  
Add this in your project `docker-compose.yml` file.

```yml
nginx:
    image: mihailbinev/nginx
    ports:
        - "80:80"
```

Of course, you should use the `volumes` to map container directories 
to your host, enable other sites, add certificate files,
manipulate log directories, etc.

```yml
nginx:
    image: mihailbinev/nginx
    ports:
        - "80:80"
    volumes:
        - /path/to/project:/var/www/PROJECT-NAME
        - <log-directory>:/var/log/nginx
        - <sites-enabled directory>:/etc/nginx/conf.d
        - <certificates directory>:/etc/nginx/certs
```

**It is important to map the path to the `PROJECT-NAME`**

Then run

```sh
docker-compose up
```

and finally visit `http://localhost/PROJECT-NAME` in your browser.


Notes
-----

The installation during the build may fail for no particular reason with this message `Failed to fetch http://httpredir.debian.org/debian/pool/main/x/xml-core...`

Just start building again.
