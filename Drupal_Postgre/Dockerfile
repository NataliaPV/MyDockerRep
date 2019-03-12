# create your custom drupal image here, based of official drupal
FROM drupal:8.2
# -y - определить автоматически да, для всех предложенных системой вопросов
# просто чистим директорию внутри машины
RUN apt-get update && apt-get install -y git \
&& rm -rf /var/lib/apt/lists/*
WORKDIR /var/www/html/themes

# качаем с гита определенный бранч с последними измениниями также 
# меняем права скаченных файлов, чтобы их можно было использовать 
# не только из-под рута
RUN git clone --branch 8.x-3.x --single-branch --depth 1 https://git.drupal.org/project/bootstrap.git \
    && chown -R www-data:www-data bootstrap

WORKDIR /var/www/html/