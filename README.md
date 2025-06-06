# TodoApp

**TodoApp** — это простой API и консольное приложение для управления задачами (ToDo), написанное на чистом Go. Реализованы две версии REST API: одна на стандартной библиотеке [`net/http`](https://pkg.go.dev/net/http), другая — с использованием [Gin](https://github.com/gin-gonic/gin). Также доступен консольный интерфейс.

---

## 🚀 Возможности

- Добавление задач
- Получение задачи по ID
- Удаление задачи
- Завершение задачи
- Получение списка всех задач
- REST API на `net/http` и `Gin`
- Консольный интерфейс
- Сохранение данных в JSON файл
- Автоматическое создание файла хранилища при первом запуске

---

## 📦 Быстрый старт

### Запуск ()

```sh
go run main.go
```

API будет доступен по адресу: [http://localhost:8989](http://localhost:8989)

---

## 🔁 Примеры REST-запросов

- Получить все задачи:
    ```
    GET /todos
    ```
- Добавить задачу:
    ```
    POST /todos
    Content-Type: application/json

    {
      "title": "Новая задача",
      "done": false
    }
    ```
- Получить задачу по ID:
    ```
    GET /todos/{id}
    ```
- Завершить задачу:
    ```
    PUT /todos/{id}
    ```
- Удалить задачу:
    ```
    DELETE /todos/{id}
    ```

---

## 🧱 Пример структуры задачи

```json
{
  "id": 1,
  "title": "Пример задачи",
  "done": false,
  "created_at": "2024-06-01T12:00:00Z"
}
```

---

## 💾 Хранение данных

Приложение сохраняет все задачи в файл `repositories/storage.json`. Файл создается автоматически при первом запуске приложения. Все изменения (добавление, удаление, обновление задач) сохраняются в этом файле.

## 🚀 Запуск приложения

### REST API (Gin)

```bash
go run main.go
```

### Консольный интерфейс

Раскомментируйте соответствующие строки в `main.go` для использования консольного интерфейса.

## 🗂 Структура проекта

```
.
├── main.go
├── go.mod
├── go.sum
├── controllers/
│   ├── controller.go
│   ├── console/              # Консольный интерфейс
│   │   ├── routes.go
│   │   └── taskController.go
│   ├── pure_rest/            # Чистый net/http
│   │   ├── errs.go
│   │   ├── handlers.go
│   │   └── routes.go
│   └── gin_rest/             # Gin фреймворк
│       ├── errs.go
│       ├── handlers.go
│       └── routes.go
├── errs/                     # Кастомные ошибки
│   └── errs.go
├── models/                   # Модели данных
│   └── task.go
├── repositories/             # Работа с данными
│   ├── memory/               # In-memory хранилище
│   │   ├── taskRepo.go
│   │   └── dummyData.go
│   ├── taskRepo.go           # Файловое хранилище (storage.json)
│   └── storage.json
├── services/                 # Бизнес-логика
│   └── taskService.go
└── utils/
    └── utils.go
```

---

## 🔧 Как это работает

- Все задачи хранятся в файле `repositories/storage.json`.
- Бизнес-логика реализована в [`services/taskService.go`](services/taskService.go).
- REST API на `net/http` — в [`controllers/pure_rest`](controllers/pure_rest/).
- REST API на `Gin` — в [`controllers/gin_rest`](controllers/gin_rest/).
- Консольный интерфейс — в [`controllers/console`](controllers/console/).

---

## 📚 Требования

- Go 1.18+

---

## 👨‍💻 Авторы

- hadisjane

---

> 🧠 Проект сделан для практики и изучения чистого Go, REST API и архитектурных подходов.
