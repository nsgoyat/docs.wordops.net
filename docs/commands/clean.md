# clean

Clean NGINX FastCGI cache, Opcache, Memcached, Redis Cache

Usage :

```bash
wo clean [options]
```

If options are empty, default is `--all`.

optional arguments | description
------------------ | -------------------------
--fastcgi          | clean Nginx fastcgi_cache |
--redis            | clean redis cache         |
--memcache         | clean memcached cache     |
--opcache          | clean opcache             |
--all              | clean all cache           |
