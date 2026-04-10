# Лабораторная работа №28. Веб-сервер на C#: список любимых игр с полным управлением

---

## Описание проекта

Веб-сервер на ASP.NET Core для управления списком игр (CRUD API).

> [!TIP]
> Проект использует хранение данных в памяти — без базы данных.

### Избранные игры

```http
GET /api/games/favourites
```

> [!NOTE]
> Работает только если есть поле `IsFavourite`

---

### Проверка пустого названия

```bash
curl -X POST http://localhost:5000/api/games \
-H "Content-Type: application/json" \
-d "{\"title\": \"\", \"genre\": \"RPG\", \"releaseYear\": 2020}"
```

> [!WARNING]
> Должен вернуться статус 400

---

## Что изучено

- Контроллеры ASP.NET Core
- CRUD операции
- HTTP методы (GET, POST, PUT, DELETE)
- Статусы HTTP
- Работа с curl

> [!TIP]
> Это базовая архитектура любого REST API

---

## Ограничения

> [!WARNING]
> Данные хранятся в памяти и исчезают после перезапуска сервера

---

## Запуск

```bash
dotnet watch run
```

> [!IMPORTANT]
> Убедись, что ты находишься в папке `GamesApi`

---

## Маршруты API

| Метод  | Маршрут         | Описание            | Статус    |
| ------ | --------------- | ------------------- | --------- |
| GET    | /api/games      | Получить все игры   | 200       |
| GET    | /api/games/{id} | Получить игру по id | 200 / 404 |
| POST   | /api/games      | Добавить игру       | 201       |
| DELETE | /api/games/{id} | Удалить игру        | 204 / 404 |
| PUT    | /api/games/{id} | Обновить игру       | 200 / 404 |

---

## Примеры curl-команд для каждого маршрута

### GET все игры

```bash
curl http://localhost:5000/api/games
```

### GET по id

```bash
curl http://localhost:5000/api/games/1
```

### POST (создание)

```bash
curl -X POST http://localhost:5000/api/games \
-H "Content-Type: application/json" \
-d "{\"title\": \"Stardew Valley\", \"genre\": \"Simulation\", \"releaseYear\": 2016}"
```

> [!WARNING]
> Не передавай Id — сервер сам его создаёт.

### PUT (обновление)

```bash
curl -X PUT http://localhost:5000/api/games/2 \
-H "Content-Type: application/json" \
-d "{\"title\": \"Updated Game\", \"genre\": \"RPG\", \"releaseYear\": 2020}"
```

### DELETE

```bash
curl -X DELETE http://localhost:5000/api/games/1
```
