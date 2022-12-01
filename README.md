Пара моментов по тестовому:
1. Сильно не заморачивался над безопаснотью ибо это тестовое и особо нет времени делать всё прям как надо
2. Чистота кода местами может хромать ибо делал все без саморевью, опять же из-за времени
3. Не гит игнорил .env, чтобы не париться с переменными окружения при развертывании
4. Webpack так же не настривал, все дефолтное
5. Под DEBUG=False тоже не подгонял, потому что бессмысленно

<b>Процесс развертывания</b>:
# Docker
 Из root директории репозитория запустить последовательно
```
docker-compose build
docker-compose up
```
Данные для входа суперюзером есть в backend/.env, но продублирую тут:
```
Логин admin
Пароль devpass
```

 # Локально (Mac OS/Linux)
 <b>Бэкенд</b><br>
 Заходим в директорию /backend. Для запуска бэка надо создать вирутальное окружение с питоном 3.9. Я использую pyenv и venv, но здесь кому
 что больше нравится. При учете, что вы в root директории репозитория и окружение называется venv (в ином случае просто активируйте окружение и запустите
 последнюю строчку):
 ```
 cd backend
 source venv/bin/activate
 pip install -r requirements.txt
 ```
 Накатываем миграции и создаем суперюзера:
 ```
 python manage.py migrate
 python manage.py createsuperuser
 ```
 Для запуска бэка активируем сначала среду, затем из нее:
 ```
 python manage.py runserver localhost:8000
 ```
 <b>Фронт</b><br>
 На фронте использую nvm для выбора нужной версии ноды:  в данном случае в проекте версия 14.0.0.
 Тут всё проще, заходим в директорию /frontend, оттуда ставим пакеты и запускаем фронт:
 ```
 npm i
 npm start
 ```
Веб морда будет по адресу <b>localhost:3000</b> и при запуске через докер, и при запуске локально :)