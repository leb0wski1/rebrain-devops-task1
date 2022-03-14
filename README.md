# Конфигурация nginx #

## Оглавление ##

- [Описание](https://github.com/leb0wski1/rebrain-devops-task1/edit/master/README.md#%D0%BE%D0%BF%D0%B8%D1%81%D0%B0%D0%BD%D0%B8%D0%B5)
- Установка и настройка
  - [Клонировать репозиторий](https://github.com/leb0wski1/rebrain-devops-task1/edit/master/README.md#%D0%BA%D0%BB%D0%BE%D0%BD%D0%B8%D1%80%D0%BE%D0%B2%D0%B0%D1%82%D1%8C-%D1%80%D0%B5%D0%BF%D0%BE%D0%B7%D0%B8%D1%82%D0%BE%D1%80%D0%B8%D0%B9) 
  - [Настройки GIT](https://github.com/leb0wski1/rebrain-devops-task1/edit/master/README.md#%D0%BD%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B9%D0%BA%D0%B8-git)
- [Записать изменения в репозиторий](https://github.com/leb0wski1/rebrain-devops-task1/edit/master/README.md#%D0%B7%D0%B0%D0%BF%D0%B8%D1%81%D0%B0%D1%82%D1%8C-%D0%B8%D0%B7%D0%BC%D0%B5%D0%BD%D0%B5%D0%BD%D0%B8%D1%8F-%D0%B2-%D1%80%D0%B5%D0%BF%D0%BE%D0%B7%D0%B8%D1%82%D0%BE%D1%80%D0%B8%D0%B9)
- [Просмотреть файл конфигурации](https://github.com/leb0wski1/rebrain-devops-task1/edit/master/README.md#%D0%BF%D1%80%D0%BE%D1%81%D0%BC%D0%BE%D1%82%D1%80%D0%B5%D1%82%D1%8C-%D1%84%D0%B0%D0%B9%D0%BB-%D0%BA%D0%BE%D0%BD%D1%84%D0%B8%D0%B3%D1%83%D1%80%D0%B0%D1%86%D0%B8%D0%B8)
- [Версия конфигурации](https://github.com/leb0wski1/rebrain-devops-task1/edit/master/README.md#%D0%B2%D0%B5%D1%80%D1%81%D0%B8%D1%8F-%D0%BA%D0%BE%D0%BD%D1%84%D0%B8%D0%B3%D1%83%D1%80%D0%B0%D1%86%D0%B8%D0%B8)

## Описание ##

В данном репозитории находится дефолтный конфигурационный файл nginx

## Клонировать репозиторий ##

[Public](https://gitlab.rebrainme.com/devops_users_repos/3679/rebrain-devops-task1.git)

## Настройки GIT ## 

:octocat: Рукомендуемые настройки после клонирования

1. `git config --local user.email "<your email>"`
2. `git config --local user.name "<your fullname>"`

## Записать изменения в репозиторий ##

Проверить состояние файлов 
- `git status`
Индексация файлов (для индексации всех файлов достаточно ввести `git add .`)
- `git add nginx.conf`
Фиксировать изменения
- `git commit -m "_your comment_"`
Отправить изменения на удаленный репозиторий
- `git push origin master`
> Когда вы хотите поделиться своими наработками, вам необходимо отправить их в удалённый репозиторий. Команда для этого действия простая: git push <remote-name> <branch-name>. Чтобы отправить вашу ветку master на сервер origin (повторимся, что клонирование обычно настраивает оба этих имени автоматически), вы можете выполнить следующую команду для отправки ваших коммитов:
## Просмотреть файл конфигурации ##

[nginx.conf](./nginx.conf)

```
user www-data;
worker_processes auto;
pid /run/nginx.pid;
include /etc/nginx/modules-enabled/*.conf;

events {
	worker_connections 768;
	# multi_accept on;
}

http {

	##
	# Basic Settings
	##

	sendfile on;
	tcp_nopush on;
	tcp_nodelay on;
	keepalive_timeout 65;
	types_hash_max_size 2048;
	# server_tokens off;

	# server_names_hash_bucket_size 64;
	# server_name_in_redirect off;

	include /etc/nginx/mime.types;
	default_type application/octet-stream;

	##
	# SSL Settings
	##

	ssl_protocols TLSv1 TLSv1.1 TLSv1.2 TLSv1.3; # Dropping SSLv3, ref: POODLE
	ssl_prefer_server_ciphers on;

	##
	# Logging Settings
	##

	access_log /var/log/nginx/access.log;
	error_log /var/log/nginx/error.log;

	##
	# Gzip Settings
	##

	gzip on;

	# gzip_vary on;
	# gzip_proxied any;
	# gzip_comp_level 6;
	# gzip_buffers 16 8k;
	# gzip_http_version 1.1;
	# gzip_types text/plain text/css application/json application/javascript text/xml application/xml application/xml+rss text/javascript;

	##
	# Virtual Host Configs
	##

	include /etc/nginx/conf.d/*.conf;
	include /etc/nginx/sites-enabled/*;
}
```

## Версия конфигурации ##

| name | version |
|------|---------|
| nginx | v0.1 |