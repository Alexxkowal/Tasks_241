# FileSystem Task1

## 1. Какие файловые системы вы знаете?

Файловые системы — это структуры, используемые для хранения, организации и управления файлами на дисках и других устройствах. Примеры файловых систем:

- **NTFS**: стандартная файловая система Windows.
- **FAT32**: старая, но совместимая файловая система.
- **exFAT**: улучшенная версия FAT32, поддерживает большие файлы.
- **EXT (EXT2, EXT3, EXT4)**: файловые системы, используемые в Linux.
- **XFS**: файловая система с высокой производительностью.
- **Btrfs**: современная файловая система с функциями моментальных снимков.

- **CIFS**: файловая система для работы с сетевыми ресурсами (Windows shares).
- **tmpfs**: временная файловая система, использующая оперативную память.

## 2. Как можно классифицировать файловые системы? В чём отличия?

Файловые системы можно классифицировать по нескольким критериям:

### По назначению:
- **Локальные**: используются для работы с локальными дисками (например, EXT4, NTFS).
- **Сетевые**: обеспечивают доступ к удалённым ресурсам (например, CIFS, NFS).
- **Виртуальные**: управляют системными данными и ресурсами (например, procfs, sysfs).

### По поддерживаемым функциям:
- **Журналируемые**: поддерживают журнал изменений для повышения надёжности (EXT3, EXT4, XFS).
- **Не журналируемые**: более простые, но менее надёжные (FAT32, EXT2).

### По поддерживаемым платформам:
- **Кроссплатформенные**: поддерживаются разными ОС (exFAT, FAT32).
- **Специфичные для ОС**: например, NTFS для Windows, EXT4 для Linux.

## 3. Какие файловые системы используются в Linux?

Основные файловые системы в Linux:

- **EXT4**: стандартная файловая система для большинства дистрибутивов Linux.
- **XFS**: подходит для больших объёмов данных и высокой производительности.
- **Btrfs**: поддерживает функции моментальных снимков и управления RAID.
- **FAT32/exFAT**: используются для совместимости с Windows.
- **CIFS**: для работы с сетевыми ресурсами (Windows shared folders).
- **tmpfs**: временные данные, хранящиеся в оперативной памяти.
- **procfs**, **sysfs**: виртуальные файловые системы для управления и мониторинга системы.

## 4. Как можно создать файловую систему на диске?

Чтобы создать файловую систему на диске, выполните следующие шаги:

1. Определить диск (например, `/dev/sdb`):

    ```bash
    lsblk
    ```

2. Создание раздела на диске (если нужно):

    ```bash
    sudo fdisk /dev/sdb
    ```

3. Создать файловую систему:

    Для EXT4:

    ```bash
    sudo mkfs.ext4 /dev/sdb1
    ```

    Для XFS:

    ```bash
    sudo mkfs.xfs /dev/sdb1
    ```

## 5. Как можно подключить диск в систему? Что такое монтирование?

Монтирование — это процесс подключения файловой системы к определённой точке (каталогу) в файловой системе.

### Подключение диска:
1. Создайте точку монтирования:

    ```bash
    sudo mkdir /mnt/mydisk
    ```

2. Подключите диск:

    ```bash
    sudo mount /dev/sdb1 /mnt/mydisk
    ```

3. Проверьте подключение:

    ```bash
    df -h
    ```

### Автоматическое монтирование при загрузке:

Добавьте запись в файл `/etc/fstab`:

```plaintext
/dev/sdb1  /mnt/mydisk  ext4  defaults  0  2
```
## 6. Особенности файловых систем procfs, cifs, tmpfs, sysfs

- **procfs**: виртуальная файловая система, предоставляющая информацию о процессах и системе. Смонтирована в `/proc`.
- **cifs**: используется для подключения сетевых ресурсов Windows. Монтируется через команду `mount -t cifs`.
- **tmpfs**: временная файловая система, которая хранит данные в оперативной памяти. Обычно монтируется в `/tmp`.
- **sysfs**: предоставляет доступ к устройствам и драйверам. Смонтирована в `/sys`.

## 7. Как можно получить информацию о системе, используя команду cat?
Информация о процессоре:
```bash
cat /proc/cpuinfo
```
Информация о состоянии памяти:
```bash
cat /proc/meminfo
```
Информация о ядре
```
cat /porc/version
```
Информация о ФС
```
cat /proc/mounts
```
