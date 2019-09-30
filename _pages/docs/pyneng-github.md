---
title: "Репозиторий курса"
permalink: /docs/pyneng-github/
---

В [репозитории курса](https://github.com/pyneng/pyneng-online-jan-apr-2019) выложены задания и примеры, которые будут рассматриваться на курсе.


Перед тем, как читать дальше, прочитайте документы:

* [Основы Git](https://pyneng.github.io/docs/git-basics/)
* [Настройка Git и GitHub](https://pyneng.github.io/docs/git-github-setup/)


### Копирование репозитория с GitHub

Все обновления в заданиях и примерах, которые выполняются по ходу курса, будут выложены в этот репозиторий.
Поэтому будет удобней скопировать локально этот репозиторий и обновлять его, когда были внесены какие-то изменения.

> Обо всех изменениях я буду говорить в Slack

Для копирования репозитория с GitHub, выполните команду git clone:
```
$ git clone https://github.com/pyneng/pyneng-online-jan-apr-2019
Cloning into 'pyneng-online-jan-apr-2019'...
remote: Counting objects: 500, done.
remote: Compressing objects: 100% (41/41), done.
remote: Total 500 (delta 20), reused 47 (delta 10), pack-reused 443
Receiving objects: 100% (500/500), 1.34 MiB | 732 KiB/s, done.
Resolving deltas: 100% (116/116), done.
```

### Обновление локальной копии репозитория

При необходимости обновить локальную версию репозитория, чтобы синхронизировать её с версией на GitHub, надо выполнить git pull внутри созданного каталога pyneng-online-jan-apr-2019.

Если обновлений не было, вывод будет таким:
```
$ cd pyneng-online-jan-apr-2019/

$ git pull
Already up-to-date.
```

Если обновления были, вывод будет примерно таким:
```
$ git pull
remote: Counting objects: 3, done.
remote: Compressing objects: 100% (1/1), done.
remote: Total 3 (delta 2), reused 3 (delta 2), pack-reused 0
Unpacking objects: 100% (3/3), done.
From https://github.com/pyneng/pyneng-online-jan-apr-2019
   49e9f1b..1eb82ad  master     -> origin/master
Updating 49e9f1b..1eb82ad
Fast-forward
 README.md | 2 +-
 1 file changed, 1 insertion(+), 1 deletion(-)
```

Обратите внимание на информацию о том, что изменился только файл README.md.

### Просмотр изменений

Если вы хотите посмотреть какие именно изменения были внесены, можно воспользоваться командой git log:
```
$ git log -p -1
commit 1eb82adb198a316f3d459f434d7e89acf66d1dba
Author: Python для сетевых инженеров <pyneng.course@gmail.com>
Date:   Mon May 29 07:42:20 2017 +0300

    Update README.md

diff --git a/README.md b/README.md
index 8435c23..f6c1583 100644
--- a/README.md
+++ b/README.md
@@ -7,5 +7,5 @@
 * [exercises](https://github.com/pyneng/pyneng-online-jan-apr-2019/tree/master/exercises) - домашние задания
 * [study](https://github.com/pyneng/pyneng-online-jan-apr-2019/tree/master/study) - ссылки и документы по обучению
-* [tools](https://github.com/pyneng/pyneng-online-jan-apr-2019/tree/master/tools) - howto по использованию инструментов курса (будут позже)
+* [tools](https://github.com/pyneng/pyneng-online-jan-apr-2019/tree/master/tools) - PDF версии howto по использованию инструментов курса (будут позже)
```

В этой команде флаг ```-p``` указывает, что мы хотим посмотреть diff изменений, а не только сообщение commit, а ```-1``` указывает, что надо показать только один commit (самый свежий).

### Посмотреть, какие изменения будут синхронизированы

Прошлый вариант опирается на количество коммитов.
Но это не всегда удобно.
До выполнения команды git pull, можно посмотреть какие изменения были выполнены с момента последней синхронизации.
Для этого используется такая команда:

```
$ git log -p ..origin/master
commit 4c1821030d20b3682b67caf362fd777d098d9126
Author: Python для сетевых инженеров <pyneng.course@gmail.com>
Date:   Mon May 29 07:53:45 2017 +0300

    Update README.md

diff --git a/tools/README.md b/tools/README.md
index 2b6f380..4f8d4af 100644
--- a/tools/README.md
+++ b/tools/README.md
@@ -1 +1,4 @@
 ## Инструменты
+
+Тут находятся PDF версии руководств по настройке инструментов, которые используются на курсе.
+Эти же руководства доступны на [сайте курса](https://pyneng.github.io/)
```

В данном случае, изменения были только в одном файле.

Эта команда будет очень полезна для того чтобы посмотреть, например, какие изменения были внесены в формулировку заданий и каких именно заданий.
Так будет легче сориентироваться касается ли это заданий, которые вы уже сделали и надо ли что-то изменить.

Если изменения были в тех заданиях, которые вы ещё не делали, этот вывод подскажет какие файлы нужно скопировать с репозитория курса в ваш личный репозиторий (а может и весь раздел, если вы еще не делали задания из этого раздела).

> ```..origin/master``` в этой команде означает показать все коммиты, которые есть в origin/master (в данном случае, это GitHub), но которых нет в вашей локальной копии репозитория.

