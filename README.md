# Установить плагин вручную

### Эта опция требует, чтобы вы управляли обновлениями вручную. Рекомендуется настроить репозиторий Docker для облегчения обслуживания.

## 1. Чтобы загрузить и установить плагин Docker Compose CLI, запустите:

* `DOCKER_CONFIG=${DOCKER_CONFIG:-$HOME/.docker}`
* `mkdir -p $DOCKER_CONFIG/cli-plugins`
* `curl -SL https://github.com/docker/compose/releases/download/v2.32.4/docker-compose-linux-x86_64 -o $DOCKER_CONFIG/cli-plugins/docker-compose`
