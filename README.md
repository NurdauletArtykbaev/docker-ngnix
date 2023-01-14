## Docker example ngnix


docker-compose up -d докер котеру
<br>
- volumes это как ярлык в компьютере
в осоновом используется для переопределения конфигов в контейнере с компьютера
volumes - примерно это прямое сообщение 
volumes:
  - ./:/var/www копиуем или дублируем весь файл в контейнер
  - ./nginx/conf.d/:/etc/nginx/conf.d копируем конфиг nginx
<br>
docker exec используется для выполнения команды в запущенном контейнере. 
 docker exec -it app_ngnix bash   - башты ашу
docker-compose down - контейнерды токтату
docker-compose images - images тер списогы

<br>
 перезапускаем nginx
 docker exec app_ngnix nginx -s reload
<br>