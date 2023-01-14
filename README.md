## Docker example ngnix


docker-compose up -d докер котеру
<br>
- volumes это как ярлык в компьютере
в осоновом используется для переопределения конфигов в контейнере с компьютера
<br>
volumes - примерно это прямое сообщение 
<br>
volumes:
  - ./:/var/www копиуем или дублируем весь файл в контейнер
  - ./nginx/conf.d/:/etc/nginx/conf.d копируем конфиг nginx
<br>
docker exec используется для выполнения команды в запущенном контейнере. 
<br>
 docker exec -it app_ngnix bash   - башты ашу
<br>
docker-compose down - контейнерды токтату
<br>
docker-compose images - images тер списогы

<br>
 перезапускаем nginx
 <br>
 docker exec app_ngnix nginx -s reload
<br>
<h3>
Ngnix не может работать на прямую с php.
Можем использовать fpm для работы ngnix с php 


</h3> 
<br>
Правила для работы с fpm

<br>
Ососбо не меняется

<br>
 location ~ \.php$ {
    try_files $uri  =404;
    fastcgi_split_path_info ^(.+\.php)(/.+)$;
    fastcgi_pass  php:9000;
    fastcgi_index index.php;
    include fastcgi_params;
    fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
    fastcgi_param PATH_INFO $fastcgi_path_info;
} 

<br>
depends_on - это сервис должен запускатса после успешного запуска php
<br>
docker: 
 depends_on:
<br>
 - php
