---
title: "Виртуальные окружения"
permalink: /docs/venv/
---


Виртуальные окружения:

* позволяют изолировать различные проекты
* зависимости, которых требуют разные проекты, находятся в разных местах
* Например, если в проекте 1 требуется пакет версии 1.0, а в проекте 2 требуется тот же пакет, но версии 3.1 пакеты, которые установлены в виртуальных окружениях, не перебивают глобальные пакеты
* позволяют удобно работать с разными версиями Python

В курсе используется virtualenvwrapper: он позволяет немного проще работать с виртуальными окружениями.

Установка virtualenvwrapper с помощью pip:
```
python3.7 -m pip install virtualenvwrapper
```

После установки, в .bashrc нужно добавить несколько строк
```
export VIRTUALENVWRAPPER_PYTHON=/usr/local/bin/python3.7
export WORKON_HOME=~/venv

. /usr/local/bin/virtualenvwrapper.sh
```

Для того чтобы скрипт virtualenvwrapper.sh выполнился и можно было работать с виртуальными окружениями, надо перезапустить bash. Например, таким образом:
```
exec bash
```

Создание виртуального окружения, в котором используется Python 3.7 (эта же команда переведет вас в виртуальное окружение):
```
mkvirtualenv --python=/usr/local/bin/python3.7 pyneng-py3
```

Установка IPython внутри виртуального окружения:
```
pip install ipython
```

После этого, можно открывать ipython (вывод должен быть примерно таким):
```
$ ipython
Python 3.7.0 (default, Jul  7 2018, 18:25:30)
Type 'copyright', 'credits' or 'license' for more information
IPython 6.4.0 -- An enhanced Interactive Python. Type '?' for help.

```

### Дополнительные возможности

При создании виртуального окружения, вывод будет таким:
```
[~]
vagrant@jessie-i386:
$ mkvirtualenv --python=/usr/local/bin/python3.7 pyneng-py3
Running virtualenv with interpreter /usr/local/bin/python3.7
Using base prefix '/usr/local'
New python executable in /home/vagrant/venv/pyneng-py3/bin/python3.7
Also creating executable in /home/vagrant/venv/pyneng-py3/bin/python
Installing setuptools, pip, wheel...done.
virtualenvwrapper.user_scripts creating /home/vagrant/venv/pyneng-py3/bin/predeactivate
virtualenvwrapper.user_scripts creating /home/vagrant/venv/pyneng-py3/bin/postdeactivate
virtualenvwrapper.user_scripts creating /home/vagrant/venv/pyneng-py3/bin/preactivate
virtualenvwrapper.user_scripts creating /home/vagrant/venv/pyneng-py3/bin/postactivate
virtualenvwrapper.user_scripts creating /home/vagrant/venv/pyneng-py3/bin/get_env_details
(venv:pyneng-py3)
[~]
vagrant@jessie-i386:

```

virtualenvwrapper указал, что он создал несколько специльных файлов.
Один из них, можно использовать, чтобы при переходе в виртуальное окружение, вас автоматически перемещало в нужный каталог.
Например, это может быть ваш репозиторий.

Файл /home/vagrant/venv/pyneng-py3/bin/postactivate отвечает за то, какие действия будут выполняться после перехода в виртуальное окружение.
По умолчанию, он пустой.

Но, если добавить в него команду ```cd /home/vagrant/online-3-natasha```, она будет автоматически выполняться каждый раз, когда вы переходите в виртуальное окружение.
И вы будете сразу и переходить в виртуальное окружение, и переходить в каталог репозитория.

Тогда вывод будет таким:
```
[~]
vagrant@jessie-i386:
$ workon pyneng-py3

(venv:pyneng-py3)
[~/online-3-natasha]
vagrant@jessie-i386:
$
```

