# docker-laravel

## laravelプロジェクトがある場合
```
docker-compose up -d
```

webappディレクトリlaravelプロジェクトを追加

/docker/nginx/default.confを変更する
```
server {
  listen 80;
    index index.php index.html;
    #    /var/www/プロジェクト名/public
    root /var/www/;

  location / {
    #    /var/www/プロジェクト名/public
    root /var/www/;
    index  index.html index.htm index.php;
    }

  location ~ \.php$ {
    #    /var/www/プロジェクト名/public
    root           /var/www/;
    fastcgi_pass   php:9000;
    fastcgi_index  index.php;
    fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
    include        fastcgi_params;
  }
 }
```

## laravelプロジェクトがない場合
```
docker-compose up -d

docker exec -it php /bin/bash

laravel new プロジェクト名
```

/docker/nginx/default.confを変更する
```
server {
  listen 80;
    index index.php index.html;
    #    /var/www/プロジェクト名/public
    root /var/www/;

  location / {
    #    /var/www/プロジェクト名/public
    root /var/www/;
    index  index.html index.htm index.php;
    }

  location ~ \.php$ {
    #    /var/www/プロジェクト名/public
    root           /var/www/;
    fastcgi_pass   php:9000;
    fastcgi_index  index.php;
    fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
    include        fastcgi_params;
  }
 }
```

