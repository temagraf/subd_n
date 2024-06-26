# Домашнее задание к занятию «`Базы данных`» - `Яковлев Артем`

### Инструкция по выполнению домашнего задания

1. Сделайте fork [репозитория c шаблоном решения](https://github.com/netology-code/sys-pattern-homework) к себе в Github и переименуйте его по названию или номеру занятия, например, https://github.com/имя-вашего-репозитория/gitlab-hw или https://github.com/имя-вашего-репозитория/8-03-hw).
2. Выполните клонирование этого репозитория к себе на ПК с помощью команды `git clone`.
3. Выполните домашнее задание и заполните у себя локально этот файл README.md:
   - впишите вверху название занятия и ваши фамилию и имя;
   - в каждом задании добавьте решение в требуемом виде: текст/код/скриншоты/ссылка;
   - для корректного добавления скриншотов воспользуйтесь инструкцией [«Как вставить скриншот в шаблон с решением»](https://github.com/netology-code/sys-pattern-homework/blob/main/screen-instruction.md);
   - при оформлении используйте возможности языка разметки md. Коротко об этом можно посмотреть в [инструкции по MarkDown](https://github.com/netology-code/sys-pattern-homework/blob/main/md-instruction.md).
4. После завершения работы над домашним заданием сделайте коммит (`git commit -m "comment"`) и отправьте его на Github (`git push origin`).
5. Для проверки домашнего задания преподавателем в личном кабинете прикрепите и отправьте ссылку на решение в виде md-файла в вашем Github.
6. Любые вопросы задавайте в чате учебной группы и/или в разделе «Вопросы по заданию» в личном кабинете.

Желаем успехов в выполнении домашнего задания.

---
### Легенда

Заказчик передал вам [файл в формате Excel](https://github.com/temagraf/subd_n/blob/main/resources/hw-12-1.xlsx), в котором сформирован отчёт. 

На основе этого отчёта нужно выполнить следующие задания.

## Задание 1

Опишите не менее семи таблиц, из которых состоит база данных:

- какие данные хранятся в этих таблицах;
- какой тип данных у столбцов в этих таблицах, если данные хранятся в PostgreSQL.

Приведите решение к следующему виду:

Сотрудники (

- идентификатор, первичный ключ, serial,
- фамилия varchar(50),
- ...
- идентификатор структурного подразделения, внешний ключ, integer).


### Перечень таблиц (3-я НФ) :
```
Проекты_имена (
- идентификатор, первичный ключ, SERIAL
- имя проекта VARCHAR(150)
)

Филиалы_адреса (
- идентификатор, первичный ключ, SERIAL
- область_id, внешний ключ, INTEGER
- город_id, внешний ключ, INTEGER
- адрес филиала, VARCHAR(350)
)

Области (
- идентификатор, первичный ключ, SERIAL
- имя района, VARCHAR(50)
)

Города (
- идентификатор, первичный ключ, SERIAL
- имя города, VARCHAR(50)
)

Подразделения_имена (
- идентификатор, первичный ключ, SERIAL
- имя подразделения, VARCHAR(150)
- тип_подразделения_id, внешний ключ, INTEGER
)

Подразделения_типы (
- идентификатор, первичный ключ, SERIAL
- тип подразделения, VARCHAR(50)
)

Должности (
- идентификатор, первичный ключ, SERIAL
- должность, VARCHAR(50)
)

Сотрудники (
- идентификатор, первичный ключ, SERIAL
- Фамилие, VARCHAR(150)
- Имя, VARCHAR(150)
- Отчество, VARCHAR(150)
- дата найма, DATA
- оклад, MONEY
- должность_id, внешний ключ, INTEGER
- подразделение_id, внешний ключ, INTEGER
- филиал_id, внешний ключ, INTEGER
)

Назначения на проекты (
- проект_id, внешний ключ, INTEGER
- сотрудник_id, внешний ключ, INTEGER
)
```

---
## Задание 2*

Перечислите, какие, на ваш взгляд, в этой денормализованной таблице встречаются функциональные зависимости и какие правила вывода нужно применить, чтобы нормализовать данные.

### Приводим к 1-й НФ
- В столбце "Проект на который назначен" убираем список
- В столбце "Адрес филиала" выделяем отдельно область/край и выделяем отдельно город

### Приводим ко 2-й НФ
- Добавляем уникальный идентификатор - первичный ключ

### Приводим к 3-й НФ
- Создаем таблицу сотрудников и таблицу проектов

---
