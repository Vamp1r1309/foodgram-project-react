# Продуктовый помощник (Foodgram)

### Описание проекта:  Foodgram - Продуктовый помощник
Добро пожаловать в Foodgram - онлайн-сервис и API, который станет вашим незаменимым помощником в кулинарных приключениях!
**Откройте новые гастрономические горизонты:** Делитесь своими уникальными рецептами, вдохновляйтесь блюдами других пользователей и делитесь своими кулинарными идеями.
**Общение и вдохновение:** Подписывайтесь на публикации других пользователей, находите новые интересные рецепты и оставляйте комментарии.
Избранное - соберите свою коллекцию: Добавляйте понравившиеся рецепты в личный список для быстрого доступа.
**Удобный список покупок:** Создайте сводный список продуктов для выбранных блюд перед походом в магазин.
Foodgram поможет вам наслаждаться гастрономическим творчеством, находить вдохновение и организовывать ваши покупки. Присоединяйтесь к нашему сообществу и начинайте свои кулинарные приключения уже сегодня!

****Foodgram - проект позволяет:****
- Просматривать рецепты
- Добавлять рецепты в избранное
- Добавлять рецепты в список покупок
- Создавать, удалять и редактировать собственные рецепты
- Скачивать список покупок

## Проект доступен по ссылкам (для ревьюера):
```
http://foodgram-project.sytes.net/
```
```
http://45.90.216.121/
```

* - примечание: данные ссылки будут работать около 1 месяца после пуша на мой github
```
## Для проверки работы сайта были добавлены админ и 2 пользователя:
#### ***Админ:***
````
почта: promining004@gmail.com
пароль: Nazarka!4
````
#### ***Пользователи:***
```
почта: ketrin_black@yandex.ru
пароль: Malinka14
```
```
почта: voices_dm@gmail.com
пароль: Grace123air
```

### **Стек:**
![python version](https://img.shields.io/badge/Python-3.10-green) ![django version](https://img.shields.io/badge/Django-4.2.1-green) ![django version](https://img.shields.io/badge/djangorestframework-3.14.0-green)

## Инструкции по установке:
#### ***1й этап - Установка на локальную машину (на ваш ПК)***

1. Клонируйте репозиторий и перейдите в него в командной строке:
```bash
git clone https://github.com/artyom-vah/foodgram-project-react
```
2. Переходим в папку backend/:
```bash
cd backend/
```
3. В папке backend/ создаем вируальное акружение venv:
```bash
python -m venv venv
```
```bash
source venv/Scripts/activate
```
или сразу так:
```bash
python -m venv venv && . venv/Scripts/activate
```
4. Обновляем менеджер пакетов pip:
```bash
python -m pip install --upgrade pip
```
5. Установите зависимости из файла requirements.txt:
```bash
pip install -r requirements.txt
```
```bash
# * - примечание: в случае если что-то не установится или будет какая-то ошибка,
# то устанавливайте по одному пакету из файла requirements.txt (у меня лично таких ошибок не было)
```
6. В случае если в infra/ нет файла.env, то создаем его в папке infra/:
```bash
cd ..
```
```bash
cd infra/
```
```bash
touch .env
```
7. В нем прописываем
```bash
TOKEN=TOKEN123 #тут можно прописать любой токен
DEBUG=False
DB_ENGINE=django.db.backends.postgresql
DB_NAME=postgres
POSTGRES_USER=postgres
POSTGRES_PASSWORD=postgres
DB_HOST=db
DB_PORT=5432
ALLOWED_HOSTS=*
TIME_ZONE=UTC
USE_TZ=True
# * - примечание: хост должен быть ALLOWED_HOSTS=*
```
8. В файле settings.py у переменной DEBUG меняем значения на True:
```bash
DEBUG = True # os.getenv('DEBUG', default=True)
```
9. В папке infra/ в файле docker-compose.yml в сервисах закоментируем image для докер-хаба:
```bash
# Должно быть так:
...
backend:
#  image: gadjet14/foodgram_backend # для запуская в облаке/на удаленном сервере
  image: foodgram_backend # для запуская на локальном компе
  ...
frontend:
#   image: gadjet14/foodgram_frontend # для запуская в облаке/на удаленном сервере
  image: foodgram_frontend # для запуская на локальном компе
  ...
* примечание - обязательно убедитесь что у вас на компе установлен докер
и докеркомпоус.
```

10. Запустим докер-файлы backend и frontend:
```bash
cd backend/
```
```bash
docker build -t foodgram_backend .
```
```bash
# в консоли будет выведено:
# [+] Building 1.9s (10/10) FINISHED
#  => [internal] load .dockerignore                                                                           0.0s
#  => => transferring context: 2B                                                                             0.0s
#  => [internal] load build definition from Dockerfile                                                        0.0s
#  => => transferring dockerfile: 278B                                                                        0.0s
#  => [internal] load metadata for docker.io/library/python:3.9-slim                                          0.6s
#  => [1/5] FROM docker.io/library/python:3.9-slim@sha256:5cde4e147c4165ad8dbf8a4df9631863766eeb0b79b890fafe  0.0s
#  => [internal] load build context
#  ...
#  => => naming to docker.io/library/foodgram_backend
```
```bash
cd frontend/
```
```bash
docker build -t foodgram_frontend .
```
```bash
# в консоли будет выведено:
# [+] Building 4.8s (12/12) FINISHED
#  => [internal] load build definition from Dockerfile       0.0s
#  => => transferring dockerfile: 201B                       0.0s
#  => [internal] load .dockerignore
#  ...
#   => => naming to docker.io/library/foodgram_frontend
```

11. Переходим в папку infra/ пересобераем контейнеры и запускаем их
```bash
cd infra/
```
```bash
docker-compose up -d --build
```
```bash
# Первый раз в консоли будет выведено:
# [+] Running 15/2
#  ✔ nginx 5 layers [⣿⣿⣿⣿⣿]     0B/0B     Pulled     9.5s
#  ✔ db 8 layers [⣿⣿⣿⣿⣿⣿⣿⣿]    0B/0B     Pulled     8.9s
# [+] Running 5/5
#  ✔ Network infra_default        Created    0.1s
#  ✔ Container infra-db-1         Started    2.6s
#  ✔ Container foodgram_frontend  Started    1.6s
#  ✔ Container foodgram_backend   Started    1.4s
#  ✔ Container foodgram_nginx     Started
```
далее при следующих запусках выполнении команды:
```bash
docker-compose up -d --build
```
```bash
# в консоли будет выведено:
# [+] Running 5/5
#  ✔ Network infra_default       Created         0s
#  ✔ Container infra-db-1        Started         8s
#  ✔ Container infra-backend-1   Started       1.3s
#  ✔ Container infra-frontend-1  Started       2.0s
#  ✔ Container infra-nginx-1     Started       3.1s
```
12. Создаем миграции и выполняемя их:
```bash
docker-compose exec backend python manage.py makemigrations
```
```bash
# в консоли будет выведено:
# Migrations for 'api':
#   api/migrations/0001_initial.py
#     - Create model FavoriteRecipe
#     - Create model Ingredient
#     - Create model Recipe
#     - Create model RecipeIngredient
#     - Create model ShoppingCart
#     - Create model Subscribe
#     - Create model Tag
#     ...
# Migrations for 'users':
#   users/migrations/0001_initial.py
#     - Create model User
```
```bash
docker-compose exec backend python manage.py migrate
```
```bash
# в консоли будет выведено:
# Operations to perform:
#   Apply all migrations: admin, api, auth, authtoken, contenttypes, sessions, users
# Running migrations:
#   Applying contenttypes.0001_initial... OK
#   Applying contenttypes.0002_remove_content_type_name... OK
#   Applying auth.0001_initial... OK
#   Applying auth.0002_alter_permission_name_max_length... OK
#   ...
#   Applying authtoken.0003_tokenproxy... OK
#   Applying sessions.0001_initial... OK
```
13. Создаем суперюзера(админа):
```bash
docker-compose exec backend python manage.py createsuperuser
```
```bash
# в консоли будет выведено:
# Email: adm@mail.ru
# Имя пользователя: adm
# Имя: adm
# Фамилия: adm
# Password:
# Password (again):
```
14. Соберем статику:
```bash
docker-compose exec backend python manage.py collectstatic --no-input
```
```bash
# в консоли будет выведено:
# 160 static files copied to '/app/static'.
```

15. Загружаем теги и ингридиенты:
```bash
docker-compose exec backend python manage.py load_tags
```
```bash
# в консоли будет выведено:
# Все тэги загружены!
```
```bash
docker-compose exec backend python manage.py load_ingrs
```
```bash
# в консоли будет выведено:
# Все ингридиенты загружены!
```
16. Переходим по адресу чтобы увидеть работу нашего сайта:
```bash
http://127.0.0.1/signin
```
17. Документация к API доступнапо адресу:
```bash
http://127.0.0.1/api/docs/
```
18. Создаем любой аккаунт, вводим:
```bash
# Например:
Имя: test
Фамилия: test
Имя пользователя: test
Адрес электронной почты: test@mail.ru
Пароль: 11test11
```
19.  Авторизуемся:
```bash
# Например:
 Электронная почта: test@mail.ru
 Пароль: 11test11
# Далее уже заходим, добавляем рецепты и пользуемся сайтом в свое удовольствие!
```

20. Остановка проекта, удаление всех контейнеров:
```bash
docker-compose down
```
```bash
# в консоли будет выведено:
# [+] Running 5/5
#  ✔ Container infra-nginx-1     Removed              0.5s
#  ✔ Container infra-frontend-1  Removed              0.0s
#  ✔ Container infra-backend-1   Removed              10.3s
#  ✔ Container infra-db-1        Removed              0.0s
#  ✔ Network infra_default       Removed              0.3s
```
<br>
