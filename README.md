# Инструкция по выполнению задач с Ansible

## 📌 Описание
Этот шаблоны Ansuble Playbook/Role  автоматизирует развертывание и настройку инфраструктуры с использованием Ansible. Включает установку и настройку различных сервисов, управление пользователями, настройку веб-серверов и балансировщиков нагрузки.

---

## ✅ Выполненные задачи

### 1️⃣ Установка и запуск Docker (`install_docker.yml`)
**Шаги:**
- Установлены необходимые пакеты.
- Добавлен репозиторий Docker.
- Установлен Docker и запущен сервис.

📌 **Используемые модули:** `apt`, `systemd`

---

### 2️⃣ Установка и запуск MySQL-сервера (`run_mysql.yml`)
**Шаги:**
- Установлен MySQL-сервер.
- Запущен и активирован сервис MySQL.

📌 **Используемые модули:** `apt`, `systemd`

---

### 3️⃣ Создание пользователя `user1`, настройка SSH-ключа и добавление файла `hosts.txt` (`ansiblevault.yml`)
**Шаги:**
- Создан пользователь `user1`.
- Добавлен SSH-ключ с использованием Ansible Vault.
- Создан инвентарь `hosts.txt` для управления хостами.

📌 **Используемые модули:** `user`, `authorized_key`, `ansible-vault`

#### 🔹 Создание файла `vault.yml` и добавление SSH-ключа:
```yaml
---
ssh_public_key: "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAACAQ..."
```

Для шифрования используйте команду:
```bash
ansible-vault encrypt vault.yml
```

#### 🔹 Создание файла `hosts.txt`:
```ini
[webservers]
web1 ansible_host=192.168.1.10 ansible_user=root
web2 ansible_host=192.168.1.11 ansible_user=root

[dbservers]
db1 ansible_host=192.168.1.20 ansible_user=root
```

📌 **Команды для работы с хостами:**
- Проверка доступности хостов:
  ```bash
  ansible all -i hosts.txt -m ping
  ```
- Выполнение команды на всех серверах:
  ```bash
  ansible all -i hosts.txt -m command -a "uptime"
  ```

---

### 4️⃣ Управление установкой и удалением Postfix (`postfix_playbook.yml`)
**Шаги:**
- При `--tags init_postfix` устанавливается и запускается Postfix.
- При `--tags drop_postfix` Postfix удаляется.

📌 **Используемые модули:** `apt`, `systemd`

---

<!--
### 5️⃣ Ansible-роль для установки FTP-сервера `vsftpd`
**Шаги:**
- Установлен FTP-сервер `vsftpd`.
- Запущен и активирован сервис.

📌 **Используемые модули:** `apt`, `systemd`

---

### 6️⃣ Ansible-роль для настройки кэширующего DNS-сервера `dnsmasq`
**Шаги:**
- Установлен `dnsmasq`.
- Настроен кэширующий DNS-сервер.
- Запущен и активирован сервис.

📌 **Используемые модули:** `apt`, `systemd`

---

### 7️⃣ Создание группы `superusers` и назначение привилегий
**Шаги:**
- Создана группа `superusers`.
- Добавлены пользователи `user2` и `user3`.
- Назначены права `sudo` с валидацией файла `sudoers`.

📌 **Используемые модули:** `group`, `user`, `lineinfile`

---

### 8️⃣ Ansible-роль для настройки `nginx+php-fpm`
**Шаги:**
- Установлены `nginx` и `php-fpm`.
- Настроен `nginx` для работы с PHP.
- Создан документ `index.php` с `phpinfo();`.

📌 **Используемые модули:** `apt`, `template`, `file`, `systemd`

---

### 9️⃣ Расширение функционала `nginx_php`
**Шаги:**
- `DocumentRoot` установлен в `/opt/nginx/ansible`.
- Добавлен handler для перезапуска `nginx` после изменений.

📌 **Используемые модули:** `file`, `copy`, `systemd`

---

## 🚀 Запуск проекта
**Шаги:**
1. Установите Ansible.
2. Настройте `ansible.cfg` и инвентарь `hosts.txt`.
3. Запустите playbook:
   ```bash
   ansible-playbook install_docker.yml
   ansible-playbook run_mysql.yml
   ansible-playbook ansiblevault.yml
   ansible-playbook postfix_playbook.yml
   ```
4. Для ролей используйте `ansible-galaxy` и `roles/`.

---

## 🛠 Используемые технологии
- **Ansible** (автоматизация развертывания)
- **YAML** (описание конфигурации)
- **Ansible Vault** (шифрование данных)
- **Nginx, MySQL, Docker, Postfix, vsftpd, dnsmasq** (развертываемые сервисы)

---

## 👥 Авторы
Проект разработан и автоматизирован с использованием Ansible.

-->
