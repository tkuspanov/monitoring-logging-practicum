# monitoring-logging-practicum
Практикум по курсу Kubernetes: мониторинг и логирование

# Ansible роли для разворачивания Prometheus и стека логирования EFK

## Описание
Репозиторий содержит Ansible роли для автоматизированного развертывания мониторинга и логирования вне Kubernetes. Установка производилась на Oracle Linux 9.
Включает роли:
- Prometheus
- Node Exporter
- Elasticsearch + Kibana
- FluentBit

## Структура репозитория
```sh
monitoring-logging-practicum/
│── roles/
│   ├── prometheus/
│   ├── node_exporter/
│   ├── elastic_kibana/
│   ├── fluentbit/
│── playbook.yml
│── README.md
```

# Запустите плейбук:
```sh
ansible-playbook playbook.yml
```

## Роли:
- prometheus: установка Prometheus, настройка мониторинга самого себя  
- node_exporter: установка и настройка Node Exporter, добавление в конфиг - Prometheus  
- elastic_kibana: установка ElasticSearch + Kibana  
- fluentbit: настройка FluentBit для сбора логов в ElasticSearch  

## Для корректной работы нужно добавить порты в firewalld или его отключить
```sh
- sudo firewall-cmd --permanent --add-port=9090/tcp
- sudo firewall-cmd --permanent --add-port=9100/tcp
- sudo firewall-cmd --permanent --add-port=9200/tcp
- sudo firewall-cmd --permanent --add-port=9300/tcp
- sudo firewall-cmd --permanent --add-port=5601/tcp
- sudo firewall-cmd --permanent --add-port=24224/tcp
- sudo firewall-cmd --permanent --add-port=24224/udp
- sudo firewall-cmd --reload
```
