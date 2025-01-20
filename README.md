version: '3.8'

services:
  git-sync:
    image: databurst/git-sync:latest
    container_name: git-sync
    restart: unless-stopped
    volumes:
      # Монтируем локальную папку /data/dags в контейнер по пути /data/dags
      - /data/dags:/data/dags
    environment:
      # URL репозитория с встроенными учетными данными для аутентификации
      REPOURL: https://git_for_airflow:glpat-2Hsh5WNtBYt_pHreoDhL@scm.sib.rual.ru/gitlab/airflow/airflow_tasks.git
      
      # Ветка, которую необходимо отслеживать
      GIT_BRANCH: main
      
      # Путь назначения внутри контейнера, куда будут синхронизированы файлы
      DESTINATION_PATH: /data/dags
      
      # Интервал синхронизации в секундах
      INTERVAL: 300  # Например, каждые 5 минут
