# homework5
```
1  Входим как root sudo su
1  Просмотр устройств lsblk
1  Создание 4 raid mirror массивов по 2 устройства в каждом
   zpool create [наименование] mirror /dev/sdb /dev/sdc
   далее пары sdd/sde, sdf/sdg, sdh/sdi
1  Просматриваем информацию о дисках zpool list
1  Добавим алгоритмы сжатия на файловые сисемы дисков
   zfs set compression=lzjb otus1
   zfs set compression=lz4 otus2
   zfs set compression=gzip-9 otus3
   zfs set compression=zle otus4
1  Проверим установку алгоритмов сжатия zfs get all | grep compression
1 Для проверки сжатия скачаем файл на все диски
   for i in {1..4}; do wget -P /otus$i https://gutenberg.org/cache/epub/2600/pg2600.converter.log; done
1  Коэфициенты сжатия отображаются по команде zfs list
1 Просмотр всех параметров файловой системы otus
   zfs get all otus
1  Определение доступного места zfs get available utus
1 Определение возможности записи zfs get readonly otus
1 Определяем размер блока zfs get recordsize otus
1 Алгоритм сжатия zfs get compression otus
1 Определение включения подсчета контрольной суммы и ее алгоритма
   zfs get checksum otus
1 Работа с snapshot.
   Скачиваем файл snapshot
   wget -O otus_task2.file --no-check-certificate https://drive.usercontent.google.com/download?id=1wgxjih8YZ-cqLqaZVa0lA3h3Y029c3oI&export=download
   Восстановим файловую систему по полученному файлу
   zfs receive otus/test@today < otus_task2.file
1 Поиск файла в директории otus/test по имени
   find /otus/test -name "secret_message"
1 Просмотр содержания найденного файла
   cat /otus/test/task1/file_mess/secret_message

   Секретное слово: ссылка на курс https://otus.ru/lessons/linux-hl/
```
