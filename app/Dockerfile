FROM python:slim
# Определяем переменные среды
# Чтобы python не создавал файлы .pyc
ENV PYTHONDONTWRITEBYTECODE=1
# Чтобы видеть выходные данные приложения в реальном времени
ENV PYTHONUNBUFFERED=1
# Устанавливаем рабочую директорию
WORKDIR /app
# Копируем в рабочую директорию файл зависимостей
COPY requirements.txt /app/

# Установливаем gcc необходимый для сборки uWSGI
RUN apt-get update && apt-get install gcc -y

# Обновляем pip устанавливаем зависимости
RUN pip install --upgrade pip
# Устанавливаем все зависимости без использования кеша
RUN pip install --no-cache-dir -r requirements.txt
# Копируем содержимое локальной директории web в рабочую директорию
COPY . /app/

# Создаём группу и пользователя UID и GUID которых мы указали в uwsgi.ini
RUN addgroup --gid 1000 web && adduser -ingroup web --uid 1000 web
# Используем только что созданого пользователя
USER web