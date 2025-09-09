**Задача 1:**
https://hub.docker.com/r/decimal0netology/custom-nginx


**Задача 2:**
![alt text](image.png)

**Задача 3:**
Контейнер останавливается, потому что был послана команда на остановку процесса. В контейнере это главный процесс с пидом 1 это энджинкс. Вот он и завершился. Ну типа, докер обслуживает только один главный процесс. Который через cmd или entrypoint запускается. Котнрол С как раз убивает этот главный процесс nginx  и контейнеру (у которого и было основное назначение nginx) больше делать нечего, поэтому он останавливается. 
![alt text](image-1.png)

Мы заменили порт в конф файле nginx, теперь он слушает не 80, а 81 порт.
![alt text](image-2.png)


Докер пробрасывает порты 8080:80, но мы поменяли в контейнере порт nginx на 81, поэтому и не работает. Либо надо в зад вернуть в конф файле, либо пересоздать контейнер с нужным пробросом портов.

можно через коммит сделать другой контейнер:
![alt text](image-3.png)

Можно остановить контейнер, докер, зайти на хосте в докер, в containers, по id зайти в конфиги контейнера, поменять в json конфигах portbindigs на порт 81 и обратно все запустить. Вроде работает.
![alt text](image-4.png)

Удалили контейнер:
![alt text](image-5.png)

**Задача 4:**
![alt text](image-7.png)

**Задача 5:**
Если есть оба файла, то сначала compose.yaml согласно докам
делаем include в compose.yaml другого файла
![alt text](image-6.png)



**compose.yaml:**
version: "3"

include:
  - docker-compose.yaml
services:
  portainer:
    network_mode: host
    image: portainer/portainer-ce:latest
    volumes:
      - /var/run/docker.sock:/var/run/docker.sock

Запушили в локальный registry:
![alt text](image-8.png)

Deployed compose:
![alt text](image-9.png)

inspect screenshot:
![alt text](image-10.png)

Гасим проект:
![alt text](image-11.png)



