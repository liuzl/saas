# saas服务

## 使用Caddy做接入

使用[zauth](https://github.com/liuzl/caddy2-zauth)和[zlog](https://github.com/liuzl/caddy2-zlog)。

```sh
xcaddy build --with github.com/liuzl/caddy2-zauth --with github.com/liuzl/caddy2-zlog
```

Caddyfile

```
{
    order zauth before respond
    order zlog before zauth
}

http://127.0.0.1:2021 {
    zauth {
        auth_db_dir ./authdb
        auth_admin_addr 127.0.0.1:198
    }
    zlog {
        log_dir ./server_zerolog
        split_by day
    }
    file_server browse
    log {
        output file ./access.log
    }
}
```

## SDK

* [Golang](https://github.com/crawlerclub/gosdk)
* [Java](https://github.com/crawlerclub/javasdk)
* [Python](https://github.com/crawlerclub/pysdk)
* [PHP](https://github.com/crawlerclub/phpsdk)

