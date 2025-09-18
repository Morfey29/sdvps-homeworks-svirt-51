# Домашнее задание к занятию "`Docker. Часть 2`" - `Дойков Анатолий`


### Оформление домашнего задания

1. Домашнее задание выполните в вашем git-репозиториий(предпочтительно) или [Google Docs](https://docs.google.com/) и отправьте на проверку ссылку на ваш документ в личном кабинете.  
1. В названии файла укажите номер лекции и фамилию студента. Пример названия: 6.4. Docker. Часть 2 — Александр Александров.
2. Код решения размещайте в отдельном файле на вашем Google-диске, это облегчит проверку вашей работы.
3. Перед отправкой проверьте, что доступ для просмотра открыт всем, у кого есть ссылка. Если нужно прикрепить дополнительные ссылки, добавьте их в свой Google Docs.

Вы можете прислать решение в виде ссылки на ваш репозийторий в GitHub, для этого воспользуйтесь [шаблоном для домашнего задания](https://github.com/netology-code/sys-pattern-homework).

**Правила выполнения заданий к занятию «6.4. Docker. Часть 2»**

- Все задания выполняйте на основе [конфигов](https://github.com/netology-code/sdvps-homeworks/tree/main/lecture_demos/6-04) из лекции. 
- В заданиях описаны те параметры, которые необходимо изменить. 
- Если параметр не упомянут вообще, значит, его нужно оставить таким, какой он был в лекции. 
- Если в каком-то задании, например, в задании 2, нужно изменить параметр, подразумевается, что во всех следующих заданиях будет использоваться уже изменённый параметр.
- Проверяйте правильность отступов. Очень важно их соблюдать, так как это влияет на структуру данных.
- Выполнив все задания без звёздочки, вы должны получить полнофункциональный сервис.

Любые вопросы по решению задач задавайте в чате учебной группы.

### Дополнительные примеры
Примеры различных композ проектов от разработчиков Docker: [https://github.com/docker/awesome-compose/blob/master/wireguard/compose.yaml](https://github.com/docker/awesome-compose/tree/master)

### Дополнительная документация:
  - [блок networks: в compose](https://docs.docker.com/compose/compose-file/06-networks/)
  - [блок volumes: в compose](https://docs.docker.com/compose/compose-file/07-volumes/)


---

### Задание 1

**Напишите ответ в свободной форме, не больше одного абзаца текста.**

Установите Docker Compose и опишите, для чего он нужен и как может улучшить лично вашу жизнь.

>Docker compose позволяет легко и быстро развернуть архетектуру с необходимой повторяемостью. Это используется как в процессе масштабирования, в процессах восстановления, так и в процессах тестирования. Лично мне это необходимо для поддержания проффесионального уровня - микросервисная архитектура является основой современных решений.

---

### Задание 2 

**Выполните действия и приложите текст конфига на этом этапе.** 

Создайте файл docker-compose.yml и внесите туда первичные настройки: 

 * version;
 * services;
 * volumes;
 * networks.

При выполнении задания используйте подсеть 10.5.0.0/16.
Ваша подсеть должна называться: <ваши фамилия и инициалы>-my-netology-hw.
Все приложения из последующих заданий должны находиться в этой конфигурации.

Скриншот к заданию 2:

![Скриншот-1](https://github.com/Morfey29/sdvps-homeworks-svirt-51/blob/main/img/img1.png)

---

### Задание 3 

**Выполните действия:** 

1. Создайте конфигурацию docker-compose для Prometheus с именем контейнера <ваши фамилия и инициалы>-netology-prometheus. 
2. Добавьте необходимые тома с данными и конфигурацией (конфигурация лежит в репозитории в директории [6-04/prometheus](https://github.com/netology-code/sdvps-homeworks/tree/main/lecture_demos/6-04/prometheus) ).
3. Обеспечьте внешний доступ к порту 9090 c докер-сервера.

---

### Задание 4 

**Выполните действия:**

1. Создайте конфигурацию docker-compose для Pushgateway с именем контейнера <ваши фамилия и инициалы>-netology-pushgateway. 
2. Обеспечьте внешний доступ к порту 9091 c докер-сервера.

---

### Задание 5 

**Выполните действия:** 

1. Создайте конфигурацию docker-compose для Grafana с именем контейнера <ваши фамилия и инициалы>-netology-grafana. 
2. Добавьте необходимые тома с данными и конфигурацией (конфигурация лежит в репозитории в директории [6-04/grafana](https://github.com/netology-code/sdvps-homeworks/blob/main/lecture_demos/6-04/grafana/custom.ini).
3. Добавьте переменную окружения с путем до файла с кастомными настройками (должен быть в томе), в самом файле пропишите логин=<ваши фамилия и инициалы> пароль=netology.
4. Обеспечьте внешний доступ к порту 3000 c порта 80 докер-сервера.

---

### Задание 6 

**Выполните действия.**

1. Настройте поочередность запуска контейнеров.
2. Настройте режимы перезапуска для контейнеров.
3. Настройте использование контейнерами одной сети.
5. Запустите сценарий в detached режиме.

---

### Задание 7 

**Выполните действия.**
1. Выполните запрос в Pushgateway для помещения метрики <ваши фамилия и инициалы> со значением 5 в Prometheus: ```echo "<ваши фамилия и инициалы> 5" | curl --data-binary @- http://localhost:9091/metrics/job/netology```.
2. Залогиньтесь в Grafana с помощью логина и пароля из предыдущего задания.
3. Cоздайте Data Source Prometheus (Home -> Connections -> Data sources -> Add data source -> Prometheus -> указать "Prometheus server URL = http://prometheus:9090" -> Save & Test).
4. Создайте график на основе добавленной в пункте 5 метрики (Build a dashboard -> Add visualization -> Prometheus -> Select metric -> Metric explorer -> <ваши фамилия и инициалы -> Apply.

В качестве решения приложите:

* docker-compose.yml **целиком**;
* скриншот команды docker ps после запуске docker-compose.yml;
* скриншот графика, постоенного на основе вашей метрики.

Содержимое compose
```yaml
version: '1.0'

volumes:
  prometheus_data: {}
  grafana_data: {}
  alertmanager_data: {}

networks:
  doykov-am-my-netology-hw:
    driver: bridge
    ipam:
      config:
        - subnet: 10.5.0.0/16

services:

  alertmanager:
    container_name: doykov-am-netology-alertmanager
    image: prom/alertmanager
    ports:
      - 9093:9093
    volumes:
      - ./alertmanager/:/etc/alertmanager/
      - alertmanager_data:/alertmanager
    networks:
      - doykov-am-my-netology-hw
    restart: unless-stopped
    command:
      - '--config.file=/etc/alertmanager/alertmanager.yml'
      - '--storage.path=/alertmanager'
    healthcheck:
      test: ["CMD", "wget", "--spider", "--quiet", "http://localhost:9093/-/healthy"]
      interval: 10s
      timeout: 5s
      retries: 3
      start_period: 10s

  cadvisor:
    container_name: doykov-am-netology-cadvisor
    image: gcr.io/cadvisor/cadvisor
    volumes:
      - /:/rootfs:ro,rslave
      - /var/run:/var/run:rw
      - /sys:/sys:ro
      - /var/lib/docker/:/var/lib/docker:ro,rslave
    ports:
      - 8080:8080
    networks:
      - doykov-am-my-netology-hw
    restart: unless-stopped
    deploy:
      mode: global
    healthcheck:
      test: ["CMD", "wget", "--spider", "--quiet", "http://localhost:8080/healthz"]
      interval: 30s
      timeout: 10s
      retries: 3
      start_period: 10s


  prometheus:
    container_name: doykov-am-netology-prometheus
    image: prom/prometheus:v2.36.2
    volumes:
      - ./prometheus/:/etc/prometheus/
      - prometheus_data:/prometheus
    command:
      - '--config.file=/etc/prometheus/prometheus.yml'
      - '--storage.tsdb.path=/prometheus'
      - '--web.console.libraries=/usr/share/prometheus/console_libraries'
      - '--web.console.templates=/usr/share/prometheus/consoles'
    ports:
      - 9090:9090
    links:
      - cadvisor:cadvisor
      - alertmanager:alertmanager
      - pushgateway:pushgateway
    depends_on:  
      alertmanager:
          condition: service_healthy
      cadvisor:
          condition: service_healthy
    networks:
      - doykov-am-my-netology-hw
    restart: on-failure:5
    healthcheck:
      test: ["CMD", "wget", "--spider", "--quiet", "http://localhost:9090/-/healthy"]
      interval: 15s
      timeout: 10s
      retries: 3
      start_period: 15s

  node-exporter:
    container_name: doykov-am-netology-node-explorer
    image: quay.io/prometheus/node-exporter:latest
    volumes:
      - /proc:/host/proc:ro
      - /sys:/host/sys:ro
      - /:/rootfs:ro,rslave
      - /:/host:ro,rslave   # Ensure using 'rslave' for /host mount
    command: 
      - '--path.rootfs=/host'
      - '--path.procfs=/host/proc'
      - '--path.sysfs=/host/sys'
      - --collector.filesystem.ignored-mount-points
      - "^/(sys|proc|dev|host|etc|rootfs/var/lib/docker/containers|rootfs/var/lib/docker/overlay2|rootfs/run/docker/netns|rootfs/var/lib/docker/aufs)($$|/)"
    ports:
      - 9100:9100
    networks:
      - doykov-am-my-netology-hw
    restart: always
    deploy:
      mode: global
    healthcheck:
      test: ["CMD", "curl", "--fail", "http://localhost:9100/metrics"]
      interval: 30s
      timeout: 10s
      retries: 3

  grafana:
    container_name: doykov-am-netology-grafana
    image: grafana/grafana
    user: "472"
    ports:
      - 80:3000
    environment:
      - GF_PATHS_CONFIG=/etc/grafana/custom.ini
    volumes:
      - grafana_data:/var/lib/grafana
      - ./grafana/custom.ini:/etc/grafana/custom.ini:ro
    networks:
      - doykov-am-my-netology-hw
    restart: unless-stopped
    depends_on:
      prometheus:
        condition: service_healthy
    healthcheck:
      test: ["CMD", "curl", "-f", "http://localhost:3000/api/health"]
      interval: 30s
      timeout: 10s
      retries: 5
      start_period: 30s

  pushgateway:
    container_name: doykov-am-netology-pushgateway 
    image: prom/pushgateway
    restart: always
    expose:
      - 9091
    ports:
      - "9091:9091"
    networks:
      - doykov-am-my-netology-hw
```
скриншот docker ps 
![Скриншот-2](https://github.com/Morfey29/sdvps-homeworks-svirt-51/blob/main/img/img2.png)

скриншот метрика grafana 
![Скриншот-3](https://github.com/Morfey29/sdvps-homeworks-svirt-51/blob/main/img/img3.png)
---

### Задание 8

**Выполните действия:** 

1. Остановите и удалите все контейнеры одной командой.

В качестве решения приложите скриншот консоли с проделанными действиями.

скриншот удаления всех контейнеров 
```
docker rm -f $(docker ps -a -q)
```

![Скриншот-4](https://github.com/Morfey29/sdvps-homeworks-svirt-51/blob/main/img/img4.png)
---

## Дополнительные задания* (со звёздочкой)

Их выполнение необязательное и не влияет на получение зачёта по домашнему заданию. Можете их решить, если хотите лучше разобраться в материале.

---

### Задание 9* 

**Выполните действия:** 

1. Создайте конфигурацию docker-compose для Alertmanager с именем контейнера <ваши фамилия и инициалы>-netology-alertmanager. 
2. Добавьте необходимые тома с данными и [конфигурацией](https://github.com/netology-code/sdvps-homeworks/tree/main/6-04/alertmanager), сеть, режим и очередность запуска.
3. Обновите конфигурацию Prometheus (необходимые изменения ищите в презентации или документации) и перезапустите его. 
4. Обеспечьте внешний доступ к порту 9093 c докер-сервера.

В качестве решения приложите скриншот с событием из Alertmanager.

событие алерт-менеджера
![Скриншот-5](https://github.com/Morfey29/sdvps-homeworks-svirt-51/blob/main/img/img5.png)
---

### Задание 10* 

Запустите свой сценарий на чистом железе без предзагруженных образов.

**Ответьте на вопросы в свободной форме:**

1. Опишите выполненный вами процесс развертывания сценария.
>
>1. Получить доступ к терминалу машины к примеру с ubuntu
>2. Установить docker/docker compose
>3. Скачать и распаковать с github проект.
>4. Выполнить сценарий compose 

2. Как вы думаете зачем может понадобиться такой способ развертывания?

>такой способ универсален для переноса, масштабирования и в целом для deploy, позволяет сэкономить время и достичь повторяемости. 
