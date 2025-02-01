# Установить плагин Docker Compose вручную

### Эта опция требует, чтобы вы управляли обновлениями вручную. Рекомендуется настроить репозиторий Docker для облегчения обслуживания.

## 1. В ОБЩЕМ, чтобы загрузить и установить плагин Docker Compose CLI, запустите:

* `DOCKER_CONFIG=${DOCKER_CONFIG:-$HOME/.docker}`
* `mkdir -p $DOCKER_CONFIG/cli-plugins`
* `curl -SL https://github.com/docker/compose/releases/download/v2.32.4/docker-compose-linux-x86_64 -o $DOCKER_CONFIG/cli-plugins/docker-compose`
### ПРИМЕЧАНИЕ. В ЧАСТНОСТИ чтобы загрузить и установить плагин Docker Compose CLI, запустите:
* Docker Compose *для всех пользователей* на вашей системе, замените 
    `~/.docker/cli-plugins` на `/usr/local/lib/docker/cli-plugins`.
* Другая версия Compose, замените `v2.32.4` на ту версию Compose, которую вы хотите использовать.
* Для другой архитектуры, замените x86_64 на нужную вам [архитектуру](https://github.com/docker/compose/releases).
