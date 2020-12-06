# AlexeyCode_infra ДЗ№5
AlexeyCode Infra repository


Подключение к внутреннему хосту через бастион в одну команду
``ssh -i appuser -At appuser@<bastion ip> ssh appuser@<internal host ip>``

Создание алиаса для подключения
Добавляем в файл(создаем если нету) `vim ~/.ssh/config` следующие записи
```
Host bastion
    HostName 178.154.231.128
    IdentityFile ~/.ssh/appuser
    Port 22
    User appuser

Host somehost
    ProxyJump bastion
    HostName 10.130.0.23
    IdentityFile ~/.ssh/appuser
    Port 22
    User appuser
```

Pritunl host with ssl - https://178.154.231.128.sslip.io/

bastion_IP = 178.154.231.128
someinternalhost_IP = 10.130.0.23

testapp_IP = 104.154.137.126
testapp_port = 9292
