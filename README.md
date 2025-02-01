# Установить с помощью репозитория apt
### Перед установкой Docker Engine на новый хост-компьютер, вам нужно настроить репозиторий Docker apt. После этого вы можете установить и обновить Docker из репозитория.
## 1. Установите репозиторий apt Docker
* Добавить официальный GPG-ключ Docker:
  
`sudo apt-get update`

`sudo apt-get install ca-certificates curl`

`sudo install -m 0755 -d /etc/apt/keyrings`

`sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc`

`sudo chmod a+r /etc/apt/keyrings/docker.asc`

* Добавить репозиторий в APT-источники:

`echo \`

  `"deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \`
  
  `$(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}") stable" | \`
  
  `sudo tee /etc/apt/sources.list.d/docker.list > /dev/null`
  
`sudo apt-get update`

## 2. Установить пакеты Docker:
* Чтобы установить последнюю версию, запустите:
`sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin`
* Чтобы установить определенную версию Docker Engine, начните с перечисления доступных версий в репозитории:
`apt-cache madison docker-ce | awk '{ print $3 }'`
`5:27.5.1-1~ubuntu.24.04~noble`
`5:27.5.0-1~ubuntu.24.04~noble`
`...`
* Выберите нужную версию и установите:
`VERSION_STRING=5:27.5.1-1~ubuntu.24.04~noble`
`sudo apt-get install docker-ce=$VERSION_STRING docker-ce-cli=$VERSION_STRING containerd.io docker-buildx-plugin docker-compose-plugin`



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
## 2. Применить права исполняемого файла к бинару:
* `chmod +x $DOCKER_CONFIG/cli-plugins/docker-compose`
  
  или, если вы установите Compose для всех пользователей:
  
* `sudo chmod +x /usr/local/lib/docker/cliplugins/docker-compose`
## 3. Проверить установку:
* `docker compose version`
  
  ожидаемый результат:
  
* `Docker Compose version v2.32.4`


 
