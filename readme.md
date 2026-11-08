# ИИ-Агент для мессенджера MAX

Сервис-помощник для учителей и учеников с интеграцией GigaChat API.

## Подготовка конфигурации

Для работы приложения требуются следующие токены доступа:
* `MAX_TOKEN` — токен доступа к мессенджеру MAX
* `GIGACHAT_CREDENTIALS` — учетные данные GigaChat API

Значения передаются при запуске контейнера через переменные окружения. Пересборка образа при смене токенов не требуется.

---

## Развертывание на другом устройстве

На целевом устройстве должен быть установлен и запущен Docker.

### Вариант 1. Запуск из файла образа (myapp.tar)

1. Загрузите образ в Docker:

```bash
docker load -i myapp.tar
```

2. Запустите контейнер, передав токены через флаги `-e`:

* Linux / macOS / Windows (PowerShell):

```powershell
docker run -d --name myapp_bot `
  -e MAX_TOKEN="ВАШ_ТОКЕН_МАКС" `
  -e GIGACHAT_CREDENTIALS="ВАШИ_CREDENTIALS_GIGACHAT" `
  myapp
```

* Windows (CMD):

```cmd
docker run -d --name myapp_bot -e MAX_TOKEN="ВАШ_ТОКЕН_МАКС" -e GIGACHAT_CREDENTIALS="ВАШИ_CREDENTIALS_GIGACHAT" myapp
```

---

### Вариант 2. Запуск с использованием файла конфигурации (.env)

1. Создайте в директории с проектом файл `.env` со следующим содержимым:

```env
MAX_TOKEN=ВАШ_ТОКЕН_МАКС
GIGACHAT_CREDENTIALS=ВАШИ_CREDENTIALS_GIGACHAT
```

2. Запустите контейнер с указанием файла конфигурации:

```bash
docker run -d --name myapp_bot --env-file .env myapp
```

---

### Вариант 3. Сборка из исходного кода

Если переносится исходный код проекта:

1. Соберите образ:

```bash
docker build -t myapp .
```

2. Запустите контейнер с передачей токенов (Вариант 1 или 2).

---

## Команды для управления контейнером

* Просмотр логов работы:

```bash
docker logs -f myapp_bot
```

* Остановка бота:

```bash
docker stop myapp_bot
```

* Запуск остановленного контейнера:

```bash
docker start myapp_bot
```

* Удаление контейнера:

```bash
docker rm -f myapp_bot
```

---

## Автоматическое создание файлов данных

Все необходимые служебные файлы (`vip.txt`, `names.txt`, `classes.txt`, `student_classes.txt`, `results.txt`) создаются автоматически при первом запуске приложения, если они отсутствуют в системе.# MAX_bot
