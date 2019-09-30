---
title: "Cloud 9"
permalink: /docs/cloud/
excerpt: "Cloud 9"
---

## Начало работы

Перед началом работы с Cloud 9, прочитайте документы:

* [Основы Git](https://pyneng.github.io/docs/git-basics/)
* [Настройка Git и GitHub](https://pyneng.github.io/docs/git-github-setup/)

### Регистрация

Для регистрации на Cloud 9 вам нужно пройти по ссылке в письме с заголовком "Team pyneng has invited you to join their team on Cloud9".

![alt]({{ site.url }}{{ site.baseurl }}/assets/images/cloud9_invite.png)

### Создание workspace

После прохождения регистрации, ваш профиль будет выглядеть так.

![alt]({{ site.url }}{{ site.baseurl }}/assets/images/cloud9_user_home.png)

Перейдите в команду PyNEng по ссылке на левой панели, под надписью "YOUR TEAM SUBSCRIPTIONS".

По этой ссылке откроется страница команды.
И список рабочих пространств команды.
Вам нужно найти такое пространство:

![alt]({{ site.url }}{{ site.baseurl }}/assets/images/cloud9_pyneng.png)


Нажмите на кнопку Clone, для создания копии рабочего пространства.

В открывшемся окне заполните поле с именем пространства.

![clone]({{ site.url }}{{ site.baseurl }}/assets/images/cloud9_cloned_workspace.png)

* workspace name - может быть любым
* Team - надо оставить PyNEng

После этого надо нажать кнопку создания рабочей области.

После создания, у workspace будет такой вид:

![first]({{ site.url }}{{ site.baseurl }}/assets/images/cloud9_workspace_first_screen.png)


## Python 3.6

В рабочем пространстве установлен Python 3.6.
Но, при клонировании, не сохраняется часть настроек [виртуального окружения](https://natenka.gitbooks.io/pyneng/content/book/01_intro/virtualenv.html).


Поэтому, чтобы использовать Python 3.6 в виртуальном окружении по умолчанию, создайте его таким образом:
```
mkvirtualenv --python=/usr/local/bin/python3.6 py3
```

### Виртуальное окружение

Перейти в виртуальное окружение:
```
workon py3
```

Выйти из виртуального окружения:
```
deactivate
```

## Настройка workspace

### Аутентификация на GitHub

Для безопасной работы с GitHub, будет использоваться аутентификацию по ключам SSH.
Каждому акаунту в Cloud 9 соответствует свой ключ, поэтому его не нужно генерировать, а достаточно просто добавить в свой акаунт GitHub.


Скопировать ключ можно в настройках профиля.
Для этого нужно перейти на страницу пользователя, а затем в правом верхнем углу нажать шестеренку.

В открывшихся настройках надо выбрать пункт SSH Keys.

![alt]({{ site.url }}{{ site.baseurl }}/assets/images/cloud9_ssh_keys.png)

А затем скопировать ключ из нижнего окна, который находится под фразой:

![alt]({{ site.url }}{{ site.baseurl }}/assets/images/cloud9_copy_ssh_key.png)

После копирования, надо перейти на GitHub.

В правом верхнем углу, на любой странице GitHub, нажмите на картинку вашего профиля и в выпадающем списке выберите Settings.

В настройках, в левой панели выберите поле "SSH and GPG keys".

Нажмите "New SSH key".
И в поле "Title" напишите название ключа (например, "Cloud 9"), а в поле "Key" вставьте содержимое, которое вы скопировали с Cloud 9.

> Если GitHub запросит пароль - введите пароль своего акаунта GitHub.


### Настройка Git

Для начала, нужно проверить текущие настройки Git.

```
$ git config --list
```

> Git уже установлен.

Главное проверить, что user.name - соответствует вашему пользователю на GitHub, а в user.email прописан email, который вы использовали для регистрации на GitHub.

Если это не так, надо установить их в правильные значения таким образом:
```
$ git config --global user.name "pyneng"
$ git config --global user.email "github_email@gmail.com"
```

Для проверки настроек, надо выполнить команду:
```
$ ssh -T git@github.com
```

Вывод будет таким:
```
Hi natenka! You've successfully authenticated, but GitHub does not provide shell access.
```

Теперь вы готовы работать с Git и GitHub.

### Копирование репозитория с GitHub

Для копирования своего репозитория с GitHub, выполните команду git clone:

```
natenka:~/workspace $ git clone ssh://git@github.com/pyneng/online-4-natasha-samoylenko.git
Cloning into 'online-4-natasha-samoylenko'...
Warning: Permanently added 'github.com,192.30.253.112' (RSA) to the list of known hosts.
remote: Counting objects: 279, done.
remote: Compressing objects: 100% (208/208), done.
remote: Total 279 (delta 74), reused 267 (delta 62), pack-reused 0
Receiving objects: 100% (279/279), 122.57 KiB | 0 bytes/s, done.
Resolving deltas: 100% (74/74), done.
```


В этой команде вам нужно сменить имя репозитория "online-4-natasha-samoylenko" на свой репозиторий.

В итоге, в текущем каталоге, в котором вы выполнили команду git clone, появится каталог с именем репозитория.
А слева, в дереве файлов появится каталог с аналогичным именем.


В остальном, принципы работы с Git и GitHub аналогичны тому, что описано в документе [Настройка Git и GitHub](https://pyneng.github.io/docs/git-github-setup/).


