---
title: "Шпаргалка pytest"
permalink: /docs/pytest-cheatsheet/
excerpt: "pytest cheatsheet"
---

### pytest.ini

Это конфигурационный файл pytest.
В нем можно настроить аргументы вызова pytest. Например, если вы хотите всегда вызывать pytest с -vv,
надо написать в pytest.ini:
```
[pytest]
addopts = -vv
```

### Полезные команды

Запуск одного теста:

```
[~/repos/pyneng-7/pyneng-online-may-aug-2019/exercises/09_functions]
vagrant: [master|✔]
$ pytest test_task_9_1.py
========================= test session starts ==========================
platform linux -- Python 3.7.3, pytest-4.6.2, py-1.5.2, pluggy-0.12.0
rootdir: /home/vagrant/repos/pyneng-7/pyneng-online-may-aug-2019/exercises/09_functions
collected 3 items

test_task_9_1.py ...                                       [100%]
...
```

Запуск одного теста с более подробным выводом информации (показывает diff между данными в тесте и тем, что получено из функции):

```
$ pytest test_task_9_1.py -vv
```

Запуск всех тестов одного раздела:

```
[~/repos/pyneng-7/pyneng-online-may-aug-2019/exercises/09_functions]
vagrant: [master|✔]
$ pytest
======================= test session starts ========================
platform linux -- Python 3.6.3, pytest-4.6.2, py-1.5.2, pluggy-0.12.0
rootdir: /home/vagrant/repos/pyneng-7/pyneng-online-may-aug-2019/exercises/09_functions
collected 21 items

test_task_9_1.py ..F                                       [ 14%]
test_task_9_1a.py FFF                                      [ 28%]
test_task_9_2.py FFF                                       [ 42%]
test_task_9_2a.py FFF                                      [ 57%]
test_task_9_3.py FFF                                       [ 71%]
test_task_9_3a.py FFF                                      [ 85%]
test_task_9_4.py FFF                                       [100%]

...
```

Запуск всех тестов одного раздела с отображением сообщений об ошибках в одну строку:

```
$ pytest --tb=line
```

## pytest-clarity

Плагин pytest-clarity улучшает отображение отличий необходимого результата с решением задания.
Его не обязательно использовать, но очень рекомендую попробовать.

Установка:
```
pip install pytest-clarity
```

Плагин pytest-clarity отрабатывает только в том случае, когда тест вызывается с флагом `-vv`.
Также по умолчанию у него довольно объемный вывод, поэтому лучше вызывать его с аргументом `--no-hints`:

```
$ pytest test_task_9_3.py -vv --no-hints
======================= test session starts ========================

test_task_9_3.py::test_function_created PASSED               [ 33%]
test_task_9_3.py::test_function_params PASSED                [ 66%]
test_task_9_3.py::test_function_return_value FAILED          [100%]

======================== FAILURES ==================================
__________ test_function_return_value ______________________________

...
        access, trunk = return_value
>       assert (
            return_value == correct_return_value
        ), "Функция возвращает неправильное значение"
E       AssertionError: Функция возвращает неправильное значение
E       assert left == right failed.
E         Showing unified diff (L=left, R=right):
E
E          L ({'FastEthernet0/0': '10',
E          R ({'FastEthernet0/0': 10,
E          L   'FastEthernet0/2': '20',
E          R   'FastEthernet0/2': 20,
E          L   'FastEthernet1/0': '20',
E          R   'FastEthernet1/0': 20,
E          L   'FastEthernet1/1': '30'},
E          R   'FastEthernet1/1': 30},
E            {'FastEthernet0/1': [100, 200],
E             'FastEthernet0/3': [100, 300, 400, 500, 600],
E             'FastEthernet1/2': [400, 500, 600]})

test_task_9_3.py:59: AssertionError
```

Так как агументы `-vv` и `--no-hints` надо постоянно передавать, можно запистаь их в pytest.ini:
```
[pytest]
addopts = -vv --no-hints
```
