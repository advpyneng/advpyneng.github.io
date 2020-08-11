---
title: "Python 3.8"
permalink: /docs/python-3-8/
excerpt: "Python 3.8"
---

### Пример установки Python 3.8 на Debian 9

Если установка выполняется на чистой ОС, лучше установить эти пакеты:
```
sudo apt-get install build-essential checkinstall
sudo apt-get install libreadline-gplv2-dev libncursesw5-dev libssl-dev
sudo apt-get install libsqlite3-dev tk-dev libgdbm-dev libc6-dev libbz2-dev libffi-dev
```

Установка Python 3.8
```
wget https://www.python.org/ftp/python/3.8.5/Python-3.8.5.tgz
tar xvf Python-3.8.5.tgz
cd Python-3.8.5
./configure --enable-optimizations --enable-loadable-sqlite-extensions
sudo make altinstall
```

После этого можно [создавать виртуальное окружение](https://pyneng.github.io/docs/venv/)
