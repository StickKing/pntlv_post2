FROM nginx:alpine
# Удаляем дефолтный файл конфигураций
RUN rm /etc/nginx/conf.d/default.conf
COPY ./nginx.conf /etc/nginx/conf.d/
# Создаём папки в которых будут храниться
# статические и медиа файлы
RUN mkdir /app
RUN mkdir /app/static
RUN mkdir /app/media