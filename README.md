# itg-test
devops junior test

Задание:

- с помощью vagrant развернуть 3 виртуальных хоста;

- используя ansible-provisioning произвести необходимую базовую настройку, развернуть на хостах docker, включить все три хоста в кластер docker-swarm;

- развернуть в контейнере службы prometheus, grafana, добавить node-exporter на каждый хост (в виде docker контейнера), cadvisor для мониторинга кластера docker-swarm;

- развернуть контейнер с nginx в качестве прокси для доступа к prometheus и grafana извне;

-  подключить хосты и swarm к мониторингу, добавить соответствующие дашбоды в grafana, добавить сервис в прокси Extra задача:

-  развернуть там же стек для работы с логами ELK (Elasticsearch + Logstash + Kibana) и подключить к нему swarm, включить стек в мониторинг.
