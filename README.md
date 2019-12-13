# monitor


### Start:

```
docker-compose up -d
```

### Stop:

```
docker-compose down
```

### Exporters

In order to let exporter to collect data, you need to:

For nginx, add these in your nginx .conf file:
    ```
    location /nginx_status {
        stub_status;
        allow 127.0.0.1;
        deny all;
    }
    ```
And restart nginx: `nginx -s reload`

For php-fpm, add these in your nginx .conf file:
    ```
    location ~ ^/(php_status|php_ping)$ {
        allow 127.0.0.1;
        deny all;
        fastcgi_pass   backend;
        include        fastcgi_params;
    }
    ```
And restart php-fpm: `/etc/init.d/php-fpm restart`


### Todo:

- Integrate with php (add php_exporter)
- Remote service monitoring
