# nginx-alpine 
только с минимальным, имхо, набором библиотек, без вброса конфигов
#COPY nginx.conf /etc/nginx/nginx.conf
#COPY nginx.vh.default.conf /etc/nginx/conf.d/default.conf

в развивающх целях предлагаеться сделать свой конфиги и вбросить их в готовый контейнер через монтирование
#  volumes:
    - ./nginx.conf:/etc/nginx/nginx.conf
    - ./default.conf:/etc/nginx/conf.d/default.conf
