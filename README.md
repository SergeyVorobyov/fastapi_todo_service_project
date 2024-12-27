# fastapi_todo_service_project
Проект сервиса ведения списка дел

Сервис реализует CRUD-операции для списка задач с хранением данных в SQLite и работой через FastAPI.
Сервис упакован в docker-контейнер.

## Эндпоинты:

POST /items: Создание задачи (title, description?, completed=false).

GET /items: Получение списка всех дел (задач).

GET /items/{item_id}: Получение задачи по ID.

PUT /items/{item_id}: Обновление задачи по ID.

DELETE /items/{item_id}: Удаление задачи

## Создание тома для хранения данных между запусками контейнера
Перед запуском контейнера необходимо создать том для хранения данных, например:

docker volume create todo_data
## Локальная сборка и запуск
Перейти в папкку с данными репозитория и запустить сборку контейнера (в конце точка):

docker build -t todo-sqlite:latest .

Запуск (с использованием ранее созданного тома):

docker run -d -p 8000:80 -v todo_data:/app/data todo-sqlite:latest

## Запуск из готового образа с docker hub
docker run -d -p 8000:80 -v todo_data:/app/data vorobyovsv/todo-service:latest

## Документация по эндпойтам
Расположена по адресу /docs, например:
http://localhost:8000/docs
