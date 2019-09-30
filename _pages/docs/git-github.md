---
title: "Добавление изменений в Git и GitHub"
permalink: /docs/git-github/
---

## Копирование репозитория с GitHub

Для выполнения заданий вы будете использовать приватный репозиторий, который создан на GitHub.

Для работы с ним локально, его нужно скопировать.
Для этого используется команда git clone:
```
$ git clone ssh://git@github.com/pyneng/online-4-natasha-samoylenko.git
Cloning into 'online-4-natasha-samoylenko'...
remote: Counting objects: 241, done.
remote: Compressing objects: 100% (191/191), done.
remote: Total 241 (delta 43), reused 239 (delta 41), pack-reused 0
Receiving objects: 100% (241/241), 119.60 KiB | 0 bytes/s, done.
Resolving deltas: 100% (43/43), done.
Checking connectivity... done.
```

В этой команде вам нужно сменить имя репозитория "online-4-natasha-samoylenko" на свой репозиторий.

В итоге, в текущем каталоге, в котором была выполнена команда git clone, появится каталог с именем равным имени репозитория.
В моем случае - online-4-natasha-samoylenko.

Если вы перейдете в этот каталог, то увидите в нем содержимое репозитория на GitHub.

## Работа с репозиторием

Предыдущая команда не просто скопировала репозиторий локально, но и настроила соответствующим образом Git:

* был создан каталог .git
* скачаны все данные репозитория
* скачаны все изменения, которые были в репозитории
* ваш репозиторий на GitHub настроен как remote для этого репозитория

Это значит, что теперь у вас готов полноценный репозиторий Git, в котором вы можете работать.

Обычно, последовательность работы будет такой:

* перед началом работы, синхронизируете локальное содержимое с GitHub командой git pull (синхронизация из GitHub в локальный репозиторий)
* редактируете какие-то файлы репозитория
* добавляете их в staging командой git add
* делаете commit с помощью git commit
* когда вы готовы закачать локальные изменения на GitHub, делаете git push

Если вы работаете с заданиями с работы и дома, надо не забывать первый и последний шаг:

* первый шаг - обновляет ваш локальный репозиторий на виртуалке
* последний шаг - загружает изменения на GitHub

### Синхронизация из GitHub в локальный репозиторий

> Все команды выполняются внутри каталога репозитория (в примере выше - online-4-natasha-samoylenko)

Команда git pull:
```
$ git pull
```

Если содержимое локального репозитория одинаково с удаленным репозиторием - GitHub, вывод будет таким:
```
$ git pull
Already up-to-date.
```

Если что-то было изменено, вывод будет примерно таким:
```
$ git pull
remote: Counting objects: 5, done.
remote: Compressing objects: 100% (1/1), done.
remote: Total 5 (delta 4), reused 5 (delta 4), pack-reused 0
Unpacking objects: 100% (5/5), done.
From ssh://github.com/pyneng/online-4-natasha-samoylenko
   89c04b6..fc4c721  master     -> origin/master
Updating 89c04b6..fc4c721
Fast-forward
 exercises/03_data_structures/task_3_3.py | 2 ++
 1 file changed, 2 insertions(+)

```

### Добавление новых файлов или изменений в существующих файлах

Добавление всех новых файлов или изменений в существующих:
```
$ git add .
```

Если необходимо добавить конкретный файл (в данном случае - README.md):
```
$ git add README.md
```

### Commit

При выполнении commit обязательно надо указать сообщение.
Будет лучше, если сообщение будет со смыслом, а не просто "update" или подобное:

```
$ git commit -m "Сделал задания 4.1-4.3"
```

### Push на GitHub

Для загрузки всех локальных изменений на GitHub, используется git push:
```
$ git push origin master
Counting objects: 5, done.
Compressing objects: 100% (5/5), done.
Writing objects: 100% (5/5), 426 bytes | 0 bytes/s, done.
Total 5 (delta 4), reused 0 (delta 0)
remote: Resolving deltas: 100% (4/4), completed with 4 local objects.
To ssh://git@github.com/pyneng/online-4-natasha-samoylenko.git
   fc4c721..edcf417  master -> master
```

> Перед выполнением git push, можно выполнить команду ```$ git log -p origin/master..``` - она покажет какие изменения вы собираетесь добавлять в свой репозиторий на GitHub.

