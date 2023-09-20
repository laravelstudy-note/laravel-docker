Laravel Docker環境
==================================

## Setup

### 1. build docker 

```
$ docker compose build
```

### 2. create laravel project

```
$ docker compose run web composer create-project laravel/laravel app
```

※ appディレクトリを作成する場合


### 3. vhostの設定

``docker/php8/vhosts.conf``のコメントアウトを解除

※ laravelのパスは環境に合わせて設定


### 4. .envの設定

```
DB_CONNECTION=mysql
DB_HOST=mysql
DB_PORT=3306
DB_DATABASE=laravel
DB_USERNAME=root
DB_PASSWORD=root
```

### 5. dockerの起動

```
$ docker compose up -d
```

## Host List

- http://localhost:8000/ -> Laravel
- http://localhost:8080/ -> phpmyadmin


## Command 

Artisanコマンドの実行(dockerに入る)

```
$ docker compose exec web /bin/sh
# cd app
# php artisan xxxxx
```


Dockerの終了

```
$ docker compose stop
```



