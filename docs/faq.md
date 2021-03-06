# F.A.Q

## General questions

### What is WordOps ?

WordOps is a command line tool which ease server administration and WordPress deployment by providing the ability to setup an optimized LEMP stack (Nginx, PHP, MySQL) with simple command like `wo stack install --nginx`.

### What are WordOps main feature ?

WordOps not only installs and configures the packages needed to deploy a site (Nginx, PHP, MariaDB) but it also takes care of creating Nginx vhosts and the database, installing WordPress and even get a Let's Encrypt SSL certificate, all in one command line.
It support multiple cache backend for WordPress, including Nginx fastcgi_cache, Redis cache (full-page cache + object cache) or wp-super-cache, based on a highly optimized Nginx configuration and an hardened security with strict location directives.

### Which operating systems are supported by WordOps ?

WordOps can be installed on Ubuntu LTS (Long Term Service) releases (16.04 & 18.04) as well as on Debian 8 (Jessie) or Debian 9 (stretch)
Support for other linux distribution isn't planned.

## Technical questions

### Which version of PHP does WordOps support ?

WordOps support PHP 7.2 (default) and PHP 7.3.

### What is the best caching solution for WordPress ?

There is no "best solution", because there are benefits/disadvantage for each caching solution and it depend on your usage.

Here some informations :

- fastcgi_cache (`--wpfc`) is the simplest solution, because it do not rely on any plugin excepted nginx_helper used to purge cache after content updates.
- redis-cache (`--wpredis`) is a powerful solution which support multi-server setup and it provide full-page cache in redis via Nginx + object-cache via Redis-Object-Cache plugin (also used to purge cache)
- wp-super-cache (`--wpsc`) is a basic solution based on a plugin which create and serve static html files.

### Why gzip compression is disabled by default ?

We disabled gzip compression by default due to gzip related security issues when using TLS connection. More informations here [BREACH CVE](https://en.wikipedia.org/wiki/BREACH). We replaced gzip by brotli, which provide better performance and compression than gzip.


## WordOps usage questions

### How to get a list of WordOps commands ?

To get the list of WordOps commands, you can use the command :

```bash
wo
```

Then for any subcommand, you just have to add the arugment -h or --help to display command informations with examples.

```bash
wo site --help
```

### What is the MySQL root password ?

MySQL root password is stored in the file `/etc/mysql/conf.d/my.cnf`

### How to change WordOps backend on port 22222 username and password ?

You can use the command :

```bash
wo secure --auth
```