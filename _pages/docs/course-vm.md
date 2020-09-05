---
title: "Виртуальная машина"
permalink: /docs/course-vm/
---

Для выполнения заданий курса можно использовать несколько вариантов:
* подготовить виртуалку самостоятельно
* работать без создания виртуальной машины
* взять подготовленную виртуалку vmware или vagrant (virtualbox)

Так как этот курс подразумевает опыт работы с Python, скорее всего,
у вас уже есть любимый редактор/IDE и среда для разработки.
Для курса лучше использовать тот вариант, который вам более привычен.
Единственное требование - использовать Python 3.8.


## Подготовленные виртуальные машины

Для курса подготовлены виртуальные машины, в которых установлены:

* Debian 9.9
* Python 3.8 в виртуальном окружении
* IPython и другие модули, которые потребуются для выполнения заданий
* текстовые редакторы vim, Geany
* GNS3 для работы с сетевым оборудованием

Сделаны два варианта подготовленных виртуальных машин:

* [Vagrant](https://docs.google.com/document/d/1Own0dJPjJfeMUCvCpIgcte_Bu63C9xuIIxLip53JPDo/edit?usp=sharing)
* [vmware](https://docs.google.com/document/d/1Is-rvPvYH8X6VY3YC5ct6fc6Bp_jfv29feng0Whnb80/edit?usp=sharing)


## Подготовка виртуальной машины/хоста самостоятельно

Если вы хотите самостоятельно подготовить виртуальную машину или работать без виртуалки, вам нужно будет установить Python 3.8.

* [Инструкция для Debian](https://pyneng.github.io/docs/python-3-8/)


И установить все необходимые модули:

```
pip install --upgrade pip ipython pytest pytest-clarity pyyaml tabulate jinja2 textfsm pexpect netmiko graphviz netmiko pexpect
pip install --upgrade asyncssh aiofiles aiohttp async-timeout more-itertools black click mypy pydantic
```
