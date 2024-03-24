1. Создан свой кастомный образ nginx на базе alpine.
Берем шаблон Dockerfile для nginx и добавляем кастомную страницу
ADD index.html /usr/share/nginx/html

```shell
user@user:~/Documents/Vagrant/19. Docker$ sudo docker build -t mynginx .
[+] Building 1.8s (8/8) FINISHED                                                                                                                                           docker:default
 => [internal] load build definition from Dockerfile                                                                                                                                 0.0s
 => => transferring dockerfile: 4.28kB                                                                                                                                               0.0s
 => [internal] load metadata for docker.io/library/nginx:1.24.0-alpine-slim                                                                                                          1.8s
 => [internal] load .dockerignore                                                                                                                                                    0.0s
 => => transferring context: 2B                                                                                                                                                      0.0s
 => [internal] load build context                                                                                                                                                    0.0s
 => => transferring context: 32B                                                                                                                                                     0.0s
 => [1/3] FROM docker.io/library/nginx:1.24.0-alpine-slim@sha256:0a8c5686d40beca3cf231e223668cf77c91344d731e7d6d34984e91a938e10f6                                                    0.0s
 => CACHED [2/3] ADD index.html /usr/share/nginx/html                                                                                                                                0.0s
 => CACHED [3/3] RUN set -x     && apkArch="$(cat /etc/apk/arch)"     && nginxPackages="         nginx=1.24.0-r1         nginx-module-xslt=1.24.0-r1         nginx-module-geoip=1.2  0.0s
 => exporting to image                                                                                                                                                               0.0s
 => => exporting layers                                                                                                                                                              0.0s
 => => writing image sha256:9b885a8e726d68950eb393e0f2bffae77d1c2b1e08b3781ce92a30e4472675f0                                                                                         0.0s
 => => naming to docker.io/library/mynginx   
```
Запускаем контейнер
```shell
sudo docker run -p 88:80 -dt mynginx
```
Проверить запущенные контейнеры.
```shell
user@user:~/Documents/Vagrant/19. Docker$ sudo docker ps -a
CONTAINER ID   IMAGE     COMMAND                  CREATED          STATUS          PORTS                               NAMES
9a9d2978fe3c   mynginx   "/docker-entrypoint.…"   27 seconds ago   Up 26 seconds   0.0.0.0:88->80/tcp, :::88->80/tcp   sweet_herschel
```

3. Образ - аналог класса, а контейнер - аналог экземпляра класса. На основе одного образа можно запустить несколько контейнеров
4. 

https://hub.docker.com/r/tomzo/buildkernel
