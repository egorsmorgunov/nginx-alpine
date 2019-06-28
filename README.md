### nginx-alpine(3.8) 
только с минимальным, имхо, набором библиотек, без вброса конфигов
### Переменные окружения 
HTTP_USER-логин для http-авторизации phpmyadmin, theia

HTTP_PASSWORD-пароль для http-авторизации phpmyadmin, theia

#### ports:
    - "80:80"
    - "443:443" 
в развивающих целях предлагаеться сделать свои конфиги и вбросить их в готовый контейнер через монтирование
####  volumes:

Обязательные:

    #конфиг nginx servers and locations
    - "/www/middlearth/conf.d/:/etc/nginx/conf.d/"
    - "/www/middlearth/html/:/var/www/html/" фалы
    - "/www/middlearth/old/:/var/www/old/"
НЕобязательные:
    
    - "/www/cert/fullchain.crt:/etc/ssl/fullchain.crt"
    - "/www/cert/privkey.key:/etc/ssl/privkey.key"
    
#### /conf.d/

    /default.conf
    
#### Синтаксис windows:
    - "/c/Users/user/default.conf:/etc/nginx/conf.d/default.conf"
, где /c/Users/user/ - папка видимая на виртуальной машине!!! (VM), где **192.168.99.100** - адрес VM по-умолчанию
#### Статический маршрут в сеть docker на VM (для просмотра результата)
    route -p add 172.0.0.0 MASK 255.0.0.0 192.168.99.100
**172.18.0.2** - возможный адрес контейнера (смотреть **docker inspect nginx**)(nginx - имя контейнера)

/usr/share/nginx/html/index.html будет доступен по адресу **172.18.0.2**, можно добавить его в hosts-файл чтобы сервер был доступен по DNS имени
