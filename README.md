# [KodiCMS](http://www.kodicms.ru/)

KodiCMS основана на базе [Kohana framework](http://kohanaframework.org/). Kohana - 
фреймворк для создания web приложений. Вы можете создавать собственные модули, 
плагины в полном объеме используя инструменты Kohana.

В качестве шаблона Backend интерфейса используется [Twitter Bootstrap](http://twitter.github.com/bootstrap/),
который позволит вам не тратить много времени на разработку шаблонов для новых
разделов.

## Ключевые особенности.

* В качестве ядра используется [Kohana framework](http://kohanaframework.org/)
* Admin интерфейс построен на базе [Twitter Bootstrap](http://twitter.github.com/bootstrap/)
* Идеальная платформа для старта крупных проектов
* Расширение при помощи плагинов
* Использование `Observer` для расширения базового функционала
* Неограниченный уровень страниц
* Высокая скорость работы
* Обработка ошибочных URL. (Если посетитель допустил ошибку URL, скорее всего он не получит в ответ: Страница не найдена)
* Удобный инсталлятор


## Скриншоты

http://www.kodicms.ru/screenshots.html



## Требования

* Apache server with .htaccess либо NGINX
* PHP 5.3.3 (или более новая)
* MySQL (и доступ к управлению данными)

## Установка
1. Создайте клон репозитория `https://github.com/butschster/kodicms.git` или 
[скачайте zip архив](https://github.com/butschster/kodicms/zipball/master)
с последней версией.

2. Разместите файлы на вашем web-сервере.

> При установке сайта не в корневую директорию, необходимо в двух местах внести изменеия.
> В файлах:
> * `.htaccess => RewriteBase /subfolder/`
> * `cms\app\bootstrap.php` => `Kohana::init( array( 'base_url' => '/subfolder/', ... ) );`

3. Откройте главную страницу через браузер. Запустится процесс интсалляции системы.

> Если возникла ошибка ErrorException [ 2 ]: date() [function.date]: It is not 
> safe to rely on the system's timezone settings. You are required to use the 
> date.timezone setting or the date_default_timezone_set() function.
> ....
> В `cms/app/bootstrap.php` есть строка `date_default_timezone_set( 'UTC' )`, 
> необходимо ее разкомментировать.
> [Доступные временные зоны](http://www.php.net/manual/timezones)

4. Заполните все необходимые поля и нажмите кнопку "Установить". 
5. После установки системы вы окажетесь на странице авторизации, где будет 
указан ваш логин и пароль для входа в систему.

### Пример конфигурации для NGINX
<pre>
server {
        charset        utf8;
        listen          80;
        root            /var/www;
        server_name     backend_node_1;
        autoindex off;
        location / {
                try_files $uri /index.php?$args;
        }
        location = /index.php {
                fastcgi_pass   127.0.0.1:9000;
                fastcgi_index  index.php;
                fastcgi_param  KOHANA_ENV production;
                fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_n$
                include        fastcgi_params;
        }
        location ~ /\.ht {
            deny all;
        }
}
</pre>

## Bug tracker

Если у вас возникли проблемы во время использования CMS, сообщайте их на наш
баг трекер.

https://github.com/butschster/kodicms/issues

## Copyright and license

Copyright 2012 Buchnev Pavel <butschster@gmail.com>.

---

KodiCMS is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

KodiCMS is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with KodiCMS.  If not, see <http://www.gnu.org/licenses/>.

KodiCMS has made an exception to the GNU General Public License for plugins.
See exception.txt for details and the full text.