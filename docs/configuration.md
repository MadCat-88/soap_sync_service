### Конфігурація вебсервісу

Конфігурація сервісу виконується у файлах `config.ini` та `alembic.ini`.

У випадку, коли вебсервіс було встановлено за допомогою скрипта, виконувати додаткових налаштувань не потрібно.

У випадку, коли вебсервіс було встановлено вручну, необхідно відредагувати зазначені файли наступним чином:



1. У файлі `alembic.ini` необхыдно выдрелагувати наступний рядок:
  ```ini
  sqlalchemy.url = mariadb+mariadbconnector://user:pass@localhost/dbname
  ```
де:

- user – логін користувача БД;
- pass – пароль даного користувача;
- dbname – назва БД.

2. У файлі `config.ini` необхідно відредагувати секцію  `[database]`, а саме наступні параметри:
  ```ini
  type = mysql
  host = your_db_host
  port = your_db_port
  name = your_db_name
  username = your_db_user
  password = your_db_password
  ```

Значення конфігурованих параметрів для файлу `config.ini` наведено нижче:

- **[database]**
  - `type`: Тип бази даних, який використовується (наприклад, mysql, postgres).
  - `host`: Хост, на якому знаходиться база даних.
  - `port`: Порт для підключення до бази даних.
  - `name`: Назва бази даних.
  - `username`: Ім'я користувача для підключення до бази даних.
  - `password`: Пароль користувача для підключення до бази даних.

- **[logging]**
  - `filename`: Шлях до файлу, в який будуть записуватися логи.
  - `filemode`: Режим роботи з файлом логів (`a` - додавання до існуючого файлу, `w` - перезапис існуючого файлу).
  - `format`: Формат запису логів. (https://docs.python.org/3/library/logging.html#logrecord-attributes)
  - `dateformat`: Формат дати та часу в логах.
  - `level`: Рівень логування (DEBUG, INFO, WARNING, ERROR, CRITICAL).

Приклад файлу конфігурації `config.ini`:

```ini
[database]
# тип бази даних (mysql, postgres тощо)
type = mysql
# хост бази даних
host = 10.0.20.242
# порт бази даних
port = 3306
# ім'я бази даних
name = soap
# ім'я користувача бази даних
username = soap
# пароль до бази даних
password = 1234

[logging]
# файл для запису логів
filename = /tmp/file.log
# режим роботи з файлом логів (a - додати, w - перезаписати)
filemode = a
# формат запису логів
format = %(asctime)s,%(msecs)d %(name)s %(levelname)s %(message)s
# формат дати і часу в логах
dateformat = %H:%M:%S
# рівень логування (DEBUG, INFO, WARNING, ERROR, CRITICAL)
level = DEBUG
```

##
Матеріали створено за підтримки проєкту міжнародної технічної допомоги «Підтримка ЄС цифрової трансформації України (DT4UA)».
