# nginx-alpine 
только с минимальным, имхо, набором библиотек, без вброса конфигов
# Переменные окружения 
LOGIN-логин для http-авторизации phpmyadmin

PASS-пароль для http-авторизации phpmyadmin

# ports:
    - "80:80"
    - "443:443"
    
в развивающих целях предлагаеться сделать свои конфиги и вбросить их в готовый контейнер через монтирование
#  volumes:
    - "./nginx.conf:/etc/nginx/nginx.conf"
    - "./default.conf:/etc/nginx/conf.d/default.conf"
# Для windows:
    - "/c/Users/user/nginx.conf:/etc/nginx/nginx.conf"
    - "/c/Users/user/default.conf:/etc/nginx/conf.d/default.conf"
, где /c/Users/user/ - папка видимая на виртуальной машине!!! (VM), где **192.168.99.100** - адрес VM по-умолчанию
#### Статический маршрут в сеть docker на VM (для просмотра результата)
    route -p add 172.0.0.0 MASK 255.0.0.0 192.168.99.100
**172.18.0.2** - возможный адрес контейнера (смотреть **docker inspect nginx**)(nginx - имя контейнера)

/usr/share/nginx/html/index.html будет доступен по адресу **172.18.0.2**, можно добавить его в hosts-файл чтобы сервер был доступен по DNS
