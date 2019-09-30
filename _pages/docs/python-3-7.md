---
title: "Python 3.7"
permalink: /docs/python-3-7/
excerpt: "Python 3.7"
---

### Пример установки Python 3.7 на Debian 9

Если установка выполняется на чистой ОС, лучше установить эти пакеты:
```
sudo apt-get install build-essential checkinstall
sudo apt-get install libreadline-gplv2-dev libncursesw5-dev libssl-dev
sudo apt-get install libsqlite3-dev tk-dev libgdbm-dev libc6-dev libbz2-dev libffi-dev
```

Установка Python 3.7
```
wget https://www.python.org/ftp/python/3.7.3/Python-3.7.3.tgz
tar xvf Python-3.7.3.tgz
cd Python-3.7.3
./configure --enable-optimizations --enable-loadable-sqlite-extensions
sudo make altinstall
```

После этого можно [создавать виртуальное окружение](https://pyneng.github.io/docs/venv/)
